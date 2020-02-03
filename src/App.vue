<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import Web3 from "web3";
const WalletConnectProvider = require("@walletconnect/web3-provider").default;

export default Vue.extend({
  name: "app",
  components: {
    HelloWorld
  },
  async mounted() {
    console.log(WalletConnectProvider);
    const provider = new WalletConnectProvider({
      infuraId: "hoge" // Required
    });

    //  Enable session (triggers QR Code modal)
    await provider.enable();
    console.log(new Web3(provider));
  }
});
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
