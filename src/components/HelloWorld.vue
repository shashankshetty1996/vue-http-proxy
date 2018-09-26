<template>
  <div class="hello">
    <h1>{{msg}}</h1>
    <button @click="loadPost()">Load Users</button>
    <ul v-if="users.length > 0">
      <li v-for="user in users" :key="user.id">
        {{user.username}}
        <hr>
      </li>
    </ul>
    <p v-else>No user loaded</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      users: []
    };
  },
  methods: {
    loadPost() {
      this.$http
        .get('/api/users')
        .then(response => response.json())
        .then(data => (this.users = data))
        .catch(err => console.log(err));
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
