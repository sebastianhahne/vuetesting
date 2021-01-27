<template>
  <div id="app">
    <Header />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offsett="3">
           <Quizbox />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Quizbox from './components/Quizbox.vue'

export default {
  name: 'App',
  components: {
    Header,
    Quizbox
  },
  data() {
    return {
      questions: []
    }
  },
  mounted: function() {
    fetch('https://opentdb.com/api.php?amount=10&type=multiple', {
      method: 'get',
    })
      .then((response) => {
        return response.json()
      })
      .then((jsonData) => {
        this.questions = jsonData.results
      })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
