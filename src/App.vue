<template>
  <div id="app" class="container">
    <h1>To-Do List</h1>
    <input id="task" v-model="newTask" type="text" value="" placeholder="Enter your task here"><br>
    <button id="btn" class="btn btn-success shadow-none" v-on:click="add">Add</button>
    <p v-if="tasks == ''">No Tasks Left</p>
    <ul>
      <li v-for="(task,i) in tasks" v-bind:key="i">
        {{ task.text }}
        <button class="btn btn-danger shadow-none float-end" v-on:click="delTask(i)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      newTask: '',
      tasks: []
    }
  },
  methods: {
    add () {
      if(this.newTask != ''){
        let idno = Math.floor((new Date()) * Math.random())
        this.tasks.push({text: this.newTask, id: idno})
        this.newTask = ''
      }
      else{
        alert('Please enter a task')
      }
    },
    delTask (i) {
      this.tasks.splice(i, 1)
    }
  }
}
</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Patrick+Hand&display=swap');

ul li{
  background-color: #5B53F8;
  color: white;
}
h1{
  font-size: 70px;
}
p{
  font-size: 40px;
  margin: 40px;
  padding: 10px;
}
input{
  background-color: white;
  border: 1px solid black;
  margin: 10px;
  font-size: 23px;
  outline: none;
  width: 50%;
  padding: 5px;
  text-align: center;
}
#btn{
  width: 50%;
  font-size: 23px;
  margin-bottom: 30px;
}
ul li{
  list-style-type: none;
  font-size: 23px;
  margin: 10px;
  padding: 10px;
  border: 1px solid black;
}
#app {
  font-family: 'Patrick Hand', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
