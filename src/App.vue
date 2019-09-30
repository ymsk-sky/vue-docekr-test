<template>
  <div>
    <Header :username='name' v-model="InputData.condition">
      <template v-slot:message>
        <p>Let's enjoy your life!</p>
      </template>
    </Header>
    <Body @add="add1"></Body>
    <Body @add="add2"></Body>
    <p>total: {{ totalcount }}</p>
    <p>condition: {{ InputData.condition }}</p>
    <button @click="componentName = 'Header'">Header</button>
    <button @click="componentName = 'Body'">Body</button>
    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>
  </div>
</template>

<script>
  import Header from './components/Header.vue'
  import Body from './components/Body.vue'

  export default {
      data() {
          return {
              name: 'piyopiyo',
              count1: 0,
              count2: 0,
              totalcount: 0,
              InputData: {
                  condition: ""
              },
              componentName: "Header"
          }
      },
      components: {
          Header,
          Body
      },
      methods: {
          add1(count) {
              this.count1 = count;
              this.totalcount = this.count1 + this.count2;
          },
          add2(count) {
              this.count2 = count;
              this.totalcount = this.count1 + this.count2;
          }
      }
  }
</script>

<style scoped>
  p {
    color: green
  }
</style>
