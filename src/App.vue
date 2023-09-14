<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>
<script>
export default {
  name: 'app',
  mounted() {
    window.addEventListener('visibilitychange',this.hac);
  },beforeDestroy() {
    window.removeEventListener('visibilitychange',this.hac)
  },
  methods:{
    hac(){
      if (document.visibilityState==='visible' && localStorage.getItem('systemAdmin')===null &&localStorage.getItem('dormitoryAdmin')===null){
        this.$router.replace({path: '/'})
      }
    }
  }
}
</script>
