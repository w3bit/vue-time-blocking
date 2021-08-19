<template>
  <div>
    <div class="hour" v-for="time in times" :key="time">
      <label>{{ time}}</label>
    </div>
    <div class="task" v-for="task in tasks" :key="task.name" :style="position(task)">
      {{ task.name }}
    </div>
    <hr/>
    <h3>Add new</h3>
    <div>
      <form>
        <input type="text" v-model="task.name" />
        <input type="number" v-model="task.start" />
        <input type="number" v-model="task.end" />
        <button type="button" @click="saveTask">Save</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TimeBlocking',
  methods: {
    position(task){
      return {
        top: (task.start * 8) + 'px',
        height: ((task.end - task.start) * 49) + 'px'
      }
    },
    saveTask(){
      this.tasks.push(Object.assign({}, this.task));
      this.task.name = '';
      this.task.start = 1;
      this.task.end = 2;
    }
  },
  data: () => {
    return {
      times: [7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 1, 2, 3],
      task: {
        name: '',
        start: 1,
        end: 2
      },
      tasks: [
      ]
    };
  },
}
</script>

<style scoped>
.hour{
  margin: 5px;
  padding: 5px;
  border-bottom: 1px solid #333;
}
.task{
  background: green;
  color: white;
  text-align: center;
  box-sizing: border-box;
  width: 200px;
  left: 100px;
  padding: 10px;
  position: absolute;
}
</style>
