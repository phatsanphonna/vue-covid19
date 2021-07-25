<template>
  <main>
    <div>
      <span>วันนี้ติดโควิดกันกี่คน ?</span>
      <h1>{{ total }}</h1>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
  name: "App",
  data() {
    return {
      total: {},
    };
  },
  async created() {
    await this.fetchData();
  },
  methods: {
    async fetchData() {
      const res: Response = await fetch(
        "https://static.easysunday.com/covid-19/getTodayCases.json"
      );
      const data = await res.json();
      this.total = data.todayCases.toLocaleString();
    },
  },
});
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Prompt:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

* {
  font-family: "Prompt", sans-serif;
  margin: 0px;
}

main {
  width: 100;
  height: 100vh;

  background-color: rgb(70, 144, 255);
  color: #ffffff;

  display: grid;
  place-items: center;
}

h1,
span {
  text-align: center;
}

h1 {
  text-align: center;
  font-size: 10rem;
}

span {
  font-size: 2rem;
}

</style>
