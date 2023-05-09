<template>
  <br><br>
  <div class="container">
    <span class="me-2">+ tambah karyawan</span><button class="btn btn-primary">Tambah</button>
    <br>
    <br>
    <h1>Daftar Karyawan.</h1>
    <div class="flex-saya">
      <div v-for="(orang, index) in karyawan" :key="index">
        <div class="card" style="width: 18rem;">
          <div class="card-img-top foto">
            <img :src="orang.avatar" class="w-foto">
          </div>
          <div class="card-body">
            <h5 class="card-title">{{ orang.first_name }} {{ orang.last_name }}</h5>
            <p class="card-text">{{ orang.email }}</p>
            <button class="btn btn-warning me-1">Edit</button> 
            <button class="btn btn-outline-danger">Hapus</button>
          </div>
        </div>
      </div>
    </div>
    </div>
    <br/><br/><br/>
</template>

<script>
// @ is an alias to /src

// fetch("https://reqres.in/api/users?page=2")
//   .then(res => res.json())
//   .then(res => console.log(res))

import axios from 'axios';

export default {
  name: "HomeView",
  data(){
    return {
      karyawan: []
    }
  },
  mounted(){
    axios.get("https://reqres.in/api/users?page=2")
      .then(res => (this.karyawan = res.data.data, console.log(res.data.data)))
  }
};
</script>

<style>
  .flex-saya {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
  }

  .foto {
    width: 100%;
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
  }

  .w-foto {
    width: 100% !important;
  }
</style>