<template>
  <div class="home">
    <div v-for="(item, index) in list" :key="index">
      <input v-model="list[index]" @keyup="save"/>
      <button @click="removeInput(index)">Delete</button>
    </div>

    <br />

    <button @click="logList">Log list</button>
    <button @click="appendInput">Add todo</button>
    <!-- <button @click="removeInput">Remove todo</button> -->
  </div>
</template>

<script>
export default {
  data () {
    return {
      list: ['']
    }
  },
  
  methods: {
    logList () {
      console.log(this.list)
    },
    
    appendInput () {
      this.list.push("")
    },

    removeInput (index) {
      this.list.splice(index, 1)
    },

    save () {
      localStorage.list = JSON.stringify(this.list)
    },

    load () {
      if (localStorage.list) this.list = JSON.parse(localStorage.list)
    },
  },

  mounted () {
    this.load()
  },
}
</script>

<style scoped>
/* .home > div::before {
  content: '';
  width: 10px;
  height: 10px;
  display: inline-block;
  background-color: blue;
} */

.home > div > button {
  opacity: 0;
}

.home > div:hover > button {
  opacity: 1;
}
</style>