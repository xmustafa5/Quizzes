<script setup>
import q from "./data/quizes.json";
import { ref, watch } from "vue";
import Card from "./components/Card.vue";
const quizzes = ref(q);
const search = ref("");

watch(search, () => {
  console.log("test");
  quizzes.value = q.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <div class="container">
    <header>
      <h1>Quizzes</h1>
      <input v-model.term="search" type="text" placeholder="search...." />
    </header>
    <div class="options-container">
      <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
}
header {
  margin-bottom: 10px;
  margin-top: 20px;
  display: flex;
  align-items: center;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
}
header input {
  border: none;
  background-color: rgba(128, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
}

.options-container {
  display: flex;
  flex-wrap: warp;
  margin-top: 40px;
}
</style>
