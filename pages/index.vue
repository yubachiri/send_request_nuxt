<template lang="pug">
section
  .container
    div
      h1.title
        | Rails API Auth Test
  .main-container
    .inline
      label(for="email_input") email: 
      input#email_input(type="text" v-model="email")
    .inline
      label(for="password_input") password: 
      input#password_input(type="text" v-model="password")
    button(@click="login") login
    p {{this.user}}
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      user: "user_data_dummy",
      email: "",
      password: "",
    };
  },
  methods: {
    login: function() {
      self = this;
      axios
        .post("http://localhost:3010/v1/login", {
          email: self.email,
          password: self.password,
        })
        .then(function(result) {
          self.user = result;
        })
        .catch(function(result) {
          console.log(result);
        });
    }
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 40vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.main-container {
  margin: 0 auto;
  min-height: 40vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.inline {
  flex-direction: row;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
