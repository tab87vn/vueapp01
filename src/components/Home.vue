<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div id="nav">
      <h2>My test navigation</h2>
      <ul>
        <li>
          <router-link to='/test01'>Test01 raw</router-link> |
          <router-link to='/test02'>Test02</router-link> |
          <router-link to='/test02/userid/123'>Test02 with param</router-link> |
          <router-link :to="{ name: 'test01-with-uid', params: { uid: 123 }}">Test01x</router-link> |
          <a @click="goTest01">Go test01 using push</a> |
          <a @click="goTest02">Go test02 using push</a> |
          <router-link to='/t03/123/three-one'>Test03 with child 1</router-link>
          <router-link to='/t03/123/three-two'>Test03 with child 2</router-link> |
          <router-link to='/test04/uid/12345'>Test04</router-link>
        </li>
      </ul>
    </div>
    <div id="sample-users">
      <ul>
        <li v-for="(user, uid) in users" v-bind:key="uid" >
          {{user.firstname}} {{user.lastname}}
        </li>
      </ul>
    </div>
    <div>
      <input type="text" v-model="input_val">
    </div>
    This is the output: <span v-text="input_val"></span>
  </div>
</template>

<script>
export default {
  name: 'home',
  data () {
    return {
      msg: 'Welcome to the awesome VueJS application',
      users: [
        {uid: 1, firstname: 'Sebastian', lastname: 'Eschweiler'},
        {uid: 2, firstname: 'Bill', lastname: 'Smith'},
        {uid: 3, firstname: 'John', lastname: 'Porter'}
      ],
      input_val: ''
    }
  },
  methods: {
    goTest01: function () {
      this.$router.push({name: 'Test01'})
    },
    goTest02: function () {
      this.$router.push({name: 'Test02', params: {uid: 123}})
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: bold;
  color: #0000FF;
}
ul {
  padding: 10;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
  text-decoration: none;
  font-weight: bold;
}

#nav {
  text-align: center;
}

#sample-users ul {
  padding: 0;
}
#sample-users li {
  display: list-item;
  list-style:circle;
  font-weight: bold;
  margin-left: 45%;
}
</style>
