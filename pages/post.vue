<template>
  <div class="main">
    <div id="example-2">
      <div class="head">
        <p>2018.11.4</p>
        <a href='/completion' class="square_btn"><button v-on:click="greet">送信</button></a>
      </div>

      <input v-model="message" placeholder="今日どんなことがあったの？">

    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {

  data: function () {
   return
 },
  methods: { //ボタンが押された時
    async greet(event) {
      let params = new URLSearchParams();
      params.append('article', this.message);
      params.append('username', 'taka');
      params.append('year', '2018');
      params.append('month', '12');
      params.append('day', '31');

      let { data } = await axios.post('http://ec2-18-191-90-196.us-east-2.compute.amazonaws.com:8080/getSentiment',params);
      console.log(data)
      console.log(this)
      // window.location.href = '/completion';
      console.log(this.message)
      console.log(data.UserName)
    }
  }
}
</script>

<style>
.main{
}

.head{
  border-bottom: medium solid #707070;
  border-width: 1px;
  /*float: left;*/
  display: flex;
  padding-top: 10px ;
  padding-bottom: 10px;
}

p{
  font-size: 39px;
  color: #767676;
  width: 60%;
  margin-left: 20%;
  text-align: center;
}

input{
  width: 100%;
  padding-left: 28px;
  padding-top: 20px;
  font-size: 20px;
}

.a{
  position: absolute;
  top:22px;
  right: 20px;
}
button{
  top:0px;
  color: white;
  font-size: 15px;
}

.square_btn{
    display: inline-block;
    padding: 1px 5px;
	  border-radius: 25px;
    text-decoration: none;
    background-color: #A5A5A5;
    margin-top: 0.5rem;
    height: 30px;
    transition: .1s;
}

.square_btn:hover {
    background-color: #707070;
}
</style>
