<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <jobs-list :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from "vue";
import JobsList from "./components/JobsList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobsList },
  setup() {
    const jobs = ref<Job[]>([
      { title: "Designer", location: "Gdansk", salary: 2000, id: "1" },
      {
        title: "React native developer",
        location: "Warsaw",
        salary: 6000,
        id: "2",
      },
      { title: "Project Manager", location: "Wroclaw", salary: 5000, id: "3" },
      { title: "Senior developer", location: "Gdansk", salary: 8000, id: "4" },
      { title: "HTML developer", location: "Gdansk", salary: 1000, id: "5" },
      { title: "C++ developer", location: "Gdansk", salary: 5000, id: "6" },
      { title: "JS engineer", location: "Gdansk", salary: 3000, id: "6" },
    ]);
    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #000000;
  border: none;
  background: rgb(241, 239, 250);
  padding: 8px 16px;
  border-radius: 5px;
  cursor: pointer;
  font-family: "Montserrat", sans-serif;
  transition: margin-right 2s;
}

button:hover {
  background: rgb(217, 209, 250);
  transform: translateY(-1px);
}
</style>
