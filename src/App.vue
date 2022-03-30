/*  This is danaXa Qualifying task for frontend developer:
    Challenge 1: Select Type Checkbox
    Author: Shahin Norouzi
    date: 3/30/2022
    Email Address: shahin.n14001995@gmail.com
*/
<template>
  <div class="w-full">
    <div class="box">
      <nav>
        <div>
          <input type="checkbox" v-model="categories" value="bounding box" id="bounding">
          <label for="bounding">
            <img src="/images/c1.svg" alt="bounding box"> 
          </label>
        </div>

        <div>
          <input disabled type="checkbox" v-model="categories" value="human" id="human">
          <label for="human">
            <img src="/images/c2.svg" alt="human">
          </label>
        </div>

        <div>
          <input type="checkbox" v-model="categories" value="box_corners" id="corners">
          <label for="corners">
            <img src="/images/c3.svg" alt="box corners">
          </label>
        </div>
      </nav>

      <div v-for="item of items" :key="item.id">
        <div v-if="this.categories.includes(item.name)" class="item">
          <div>
            <img :src="item.icon" width="29">
          </div>
          <div v-text="item.name"></div>
          <select v-model="item.value">
            <option v-for="n of 44" :key="n" :value="n">{{ n }}</option>
          </select>
        </div>
      </div>

      <div v-show="this.categories.length < 1" style="text-align:center;padding:50px 0;color:gray">
        No Items!
      </div>
      
    </div>
  </div>
</template>

<script>
import { api } from './api.js';

export default {
  name: 'App',
  data(){
    return{
      categories:["bounding box", "box_corners"],
      items: api
    }
  }
}
</script>

<style>
  body{
    background-color: #222222;
  }
  .w-full{
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .box{
    background-color: #282930;
    width: 30%;
    min-width: 300px;
    margin-top: 30px;
  }
  nav{
    display: flex;
    justify-content: space-evenly;
    padding: 10px 0;
    border-bottom: 1px solid gray;
  }
  nav div{
    display:inline-flex;
    margin:auto 0;
  }
  [type=checkbox]{
    -ms-transform: scale(1.8); /* IE */
    -moz-transform: scale(1.8); /* FF */
    -webkit-transform: scale(1.8); /* Safari and Chrome */
    -o-transform: scale(1.8); /* Opera */
    transform: scale(1.8);
    margin: 0;
  }
  [type=checkbox]:not([disabled]), [type=checkbox]:not([disabled]) + label{
    cursor: pointer;
  }
  .item{
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: white;
    padding: 15px 20px;
    font-size: 18px;
  }
  .item:hover{
    background-color: #333344;
  }
  select{
    background: #282930;
    border-radius: 5px;
    border: 1px solid rgb(70, 70, 70);
    color: white;
    padding: 2px 5px;
    font-size: 16px;
  }
  nav img{
    margin-left: 16px;
  }
  input[disabled] + label{
    opacity: .4;
  }
</style>
