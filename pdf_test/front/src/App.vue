<template>
  <div id="app">
    <button @click="generateReport()">generate pdf</button>
    <vuehtlm2pdf
      :show-layout="true"
      :float-layout="false"
      :enable-download="true"
      :preview-modal="true"
      :paginate-elements-by-height="1400"
      filename="hee hee"
      :pdf-quality="2"
      :manual-pagination="false"
      pdf-format="a4"
      pdf-orientation="portrait"
      pdf-content-width="800px"

      @progress="onProgress()"
      @hasStartedGeneration="hasStartedGeneration()"
      @hasGenerated="hasGenerated($event)"

      ref="html2Pdf"
    >
      <section slot="pdf-content">
        
        <div id="nav">
          <router-link to="/">Home</router-link> |
          <router-link to="/about">About</router-link>
        </div>
        <router-view/>
      
      </section>
    </vuehtlm2pdf>
  </div>
</template>


<script>
import vuehtlm2pdf from 'vue-html2pdf'

export default {
  name: 'App',
  methods: {
    generateReport() {
      this.$refs.html2Pdf.generatePdf()
    },
    onProgress() {
      console.log('working')
    },
    hasStartedGeneration() {
      console.log('started')
    },
    hasGenerated() {
      console.log('finished')
    }
  },
  components: {
    vuehtlm2pdf
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
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
