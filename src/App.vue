<template>
  <div id="app">
    <div class="contador">
      <h1>{{contadorSeg < 10 ? '0'+contadorSeg : contadorSeg }}</h1>
      <h2>segundos</h2>
    </div>
    <div class="botones">
      <button @click="iniciar(5)">5 segs</button>
      <button @click="iniciar(10)">10 segs</button>
      <button @click="iniciar(30)">30 segs</button>
      <button @click="iniciar(60)">1 min</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Timer",

  data() {
    return {
      contadorSeg: 0,
      intervalo: 0,
    };
  },

  methods: {
    iniciar(time) {
      this.contadorSeg = time;
      clearInterval(this.intervalo);

      this.intervalo = setInterval(() => {
        this.contadorSeg > 0 ? this.contadorSeg-- : false;
      }, 1000);

      setTimeout(() => {
        clearInterval(this.intervalo);
      }, (time + 1) * 1000);
    },
  },
};
</script>

<style lang="scss">
body {
  min-height: 100vh;
  background-color: #14213d;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1,
h2 {
  margin: 0;
}
h1 {
  font-size: 40px;
}
h2 {
  font-size: 20px;
}
button {
  padding: 10px 25px;
  color: #14213d;
  cursor: pointer;
  border-radius: 5px;
  &:hover {
    background-color: #e5e5e5;
  }
  &:focus {
    background-color: #fca311;
    font-weight: 600;
  }
}
.contador {
  margin: 0 auto;
  background-color: #fca311;
  color: #000;
  border-radius: 50%;
  width: 150px;
  height: 150px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 30px;
}
</style>
