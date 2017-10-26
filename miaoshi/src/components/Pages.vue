<template>
  <div class="pagination">
    <span class="totle">共{{totlePages}}条，每页20条</span>
    <img class="img" :src="pnextUrl" alt=""><span class="num">{{mynowPages}}/{{Math.ceil(mytotlePages/20)}}</span>
    <img class="img" :src="nextUrl" alt="">
    <input type="" name="" v-model="pagesJump">
    <span class="jump" @click="Jump">跳转</span>
  </div>
</template>

<script>
import ic_nextActive from '@/assets/ic_next_pressed@1x.png'
import ic_next from '@/assets/ic_next_normal@1x.png'
import pic_next from '@/assets/ic_pre_normal@1x.png'
import pic_nextActive from '@/assets/ic_pre_pressed@1x.png'

export default {
  name: 'Pages',
  data () {
    return {
      nextUrl:ic_next,
      nextUrlA:ic_nextActive,
      pnextUrl:pic_next,
      pnextUrlA:pic_nextActive,
      pagesJump:'',
      mynowPages:this.nowPages,
      mytotlePages:this.totlePages
    }
  },
  props:["totlePages","nowPages"],
  mounted(){
  },
  watch:{
    mynowPages(val){
      this.$emit('update:nowPages', val)
    },
    mytotlePages(val){
      this.$emit('update:totlePages', val)
    },
    totlePages(val){
      this.totlePages = val
    },
    nowPages(val){
      this.nowPages = val
    }
  },
  // computed:{
  //   mytotlePages(){
  //     return this.totlePages
  //   },
  //   mynowPages(){
  //      return this.nowPages
  //   }
  // },
  methods:{
    Jump(){
      this.mynowPages = this.pagesJump
    }
  }
}
</script>

<style lang="scss" scoped>
	.pagination{
	}
</style>
