<template>
  <div class="landing-page">
      <div class="container">
      <div class="row align-items-center pb-5">
          <!-- Column 1: Image -->
          <div class="col-lg-5">
          <img src="/src/assets/roadmap.png" alt="Roadmap" class="img-fluid roadmapImg" />
          </div>
  
          <!-- Column 2: Title, Subtitle, and Prompt Bar -->
          <div class="col-lg-7">
          <h1 class="title mb-2">Welcome Back!</h1>
          <p class="subtitle mb-4">Please enter your details.</p>

          <form @submit.prevent="submitData">
  
            <!-- Email -->
            <div class="search-container">
                <input 
                type="text" 
                class="search-input" 
                v-model="username" 
                placeholder="  Email"
                />
            </div>

            <!-- Password -->
            <div class="search-container">
                <input 
                type="password" 
                class="search-input" 
                v-model="password" 
                placeholder="  Password"
                />
            </div>

            <button class="loginBtn" type="submit">LOGIN</button>
            </form>
  
          </div>
      </div>
      </div>
  </div>
</template>

<script>

import axios from 'axios';

export default {
  data() {
    return {
      username: '',
      password: ''
    };
  },

  methods: {
    async submitData() {
      try {
        const response = await axios.post('http://localhost/login', {
          username: this.username,
          password: this.password
        });
        console.log('Response:', response.data);
        if(response.data.status == "success") {
            this.$router.push('/dashboard');
        } else {
            console.log("BURAT");
        }
      } catch (error) {
        console.error('There was an error!', error);
      }
    }
  }
};
</script>

<style scoped>
@import './LoginPage.css';  


html, body, .landing-page {
  height: 100%;
  margin: 0;
}

.loginBtn{
  background: linear-gradient( #30D6F3, #2EBBD4);
  border: none; 
  color: white;
  padding: 15px;
  width: 100%;
  text-align: center;
  border-radius: 30px;
  font-size: 18px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.loginBtn:hover{
  background: linear-gradient(90deg, #2EBBD4, #30D6F3); 
}

</style>
