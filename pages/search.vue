<template lang="html">
  <div class="page">
    Page is Search
    <ul>
      <li v-for="(item,index) in $store.state.navbar.app" :key="index">{{item}}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  layout: 'search',
  data () {
    return {
      list: []
    }
  },
  async asyncData () {
    let {status, data: {list}} = await axios.get('http://localhost:3000/city/list')
    if (status === 200) {
      return {
        list
      }
    }
  }
  // async mounted () {
  //   let self = this
  //   let {status, data: {list}} = await axios.get('/city/list')
  //   if (status === 200) {
  //     self.list = list
  //   }
  // }
}
</script>

<style lang="css" scoped>
</style>
