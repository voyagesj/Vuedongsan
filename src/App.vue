<template>

<div class="black-bg" v-if="isModalOpen">
  <div class="white-bg">
    <h4>상세페이지임</h4>
    <p>상세페이지 내용임</p>
    <!-- input type="text" :value="inputData" v-on:keyup="saveInputData" /-->
    <input type="text" v-model="inputData" />
    <button v-on:click="closeModal">닫기</button>
  </div>
</div>

  <div class="menu">
    <a v-for="(m,i) in menus" :key="i">{{m}}{{ i }}</a>
  </div>

  <div v-for="(p,i) in rooms" :key="i">
    <img :src=p.image class="room-img" />
    <h4 v-on:click="openModal">{{p.title}}</h4>    
    <p>{{p.content}}</p>
    <p>{{p.price}}</p>
    <button v-on:click=" increase(i)">허위매물신고</button>
    <span>신고수:{{ productsSingo[i] }}</span>
  </div>
  


</template>

<script>
import oneroomData from './assets/oneroom.jsroom.js';

export default {
  name: 'App',
  data() {
    return {
      isModalOpen:false,
      rooms: oneroomData,
      menus:['home','Products','About'],
      productsSingo:[0,0,0],
      inputData:'hello'
    }
  },
  methods:{
    increase(d){this.productsSingo[d]++;},
    openModal(){this.isModalOpen = true;},
    closeModal(){this.isModalOpen = false;},
    saveInputData(e){this.inputData = e.target.value},
  },
  components: {
  }
}
</script>

<style>
body{
  margin:0;
}
div{box-sizing:border-box;}
.black-bg{
  width:100%; height: 100%; background:rgba(0,0,0,0.5); position:fixed;padding:20px;
}
.white-bg{
  width:100%;background: white;border-radius: 8px;padding:20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background:darkslateblue;
  padding:15px;
  border-radius: 5px;  
}
.menu a{
  color:white;
  padding:10px;
}
.room-img{
  width:100%;
  margin-top:50px;
}
</style>
