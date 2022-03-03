<template>
  <div class="container">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <h1>Filters</h1>
        <p>{{ text | capitalize }}</p>
        <input type="text" v-model="text">
        <hr />
        <input v-model="filterText" />
        <ul>
          <li v-for="fruit in filteredFruits">{{ fruit }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "harry!",
      fruits: ["Apple", "Banana", "Mango", "Melon"],
      filterText: "",
    };
  },
  filters: {
    capitalize(value) {
      if (!value) return "";
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    },
  },
  computed: {
    filteredFruits() {
      return this.fruits.filter((element) => {
        return element.match(this.filterText);
      });
    },
  },
};
</script>

<style>
</style>
