<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by Title</button>
        <button @click="handleClick('location')">Order by Location</button>
        <button @click="handleClick('salary')">Order by Salary</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from "vue";
import Job from "@/types/Jobs";
import JobList from "@/components/JobList.vue";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "Farm worker",
        location: "lon lon ranch",
        salary: 2000,
        id: "1",
      },
      {
        title: "quarryman",
        location: "death mountain",
        salary: 40000,
        id: "2",
      },
      {
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
        id: "3",
      },
      { title: "fisherman", location: "lake hyliaaa", salary: 21000, id: "4" },
      {
        title: "prison guard",
        location: "gerudo valley",
        salary: 32000,
        id: "5",
      },
    ]);
    const order = ref<OrderTerm>("title"); // get the valid types in the OrderTerm

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return { jobs, handleClick, order };
  },
  methods: {},
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
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
