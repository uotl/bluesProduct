<template>
  <div class="content">
    <p class="title">{{title}}</p>
    <div class="iptBox">
      <input class="todoIpt" type="text" v-model="addTodoTxt">
      <span class="addBtn" @click="add">添加</span>
    </div>
    <p class="clear" @click="clear">清空</p>
    <div class="todoLists">
      <p :class="{'underLine':item.done,'todoItem':true}" v-key="i" v-for="(item,i) in todos" @click="changeDone(i)">{{item.title}}</p>
    </div>
    <p class="showPro">{{nums}} / {{todos.length}}</p>
  </div>
</template>

<script>

export default {
  data () {
    return {
      title:'hello mpvue',
      addTodoTxt: '',
      todos:[
        {title:'吃饭',done:false},
        {title:'睡觉',done:false},
      ]
    }
  },

  components: {
  },

  methods: {
    add() {
      if(!this.addTodoTxt){
        return
      }else{
        this.todos.push({title:this.addTodoTxt,done:false})
      }
      this.addTodoTxt = '';
    },
    changeDone(i) {
      this.todos[i].done = !this.todos[i].done
    },
    clear() {
      this.todos = this.todos.filter(v => !v.done);
    }
  },
  computed: {
    nums () {
      return this.todos.filter(v => !v.done).length
    }
  },
  created () {
  }
}
</script>

<style scoped lang="less">
.content {
  .title{
    color: aqua;
  }
  .underLine{
    text-decoration: line-through;
  }
  .iptBox{
    overflow: hidden;
    .todoIpt{
      width: 70%;
      float: left;
      border: 1px solid #000;
    }
    .addBtn{
      width: 20%;
      float: right;
    }
  }
  
}
</style>
