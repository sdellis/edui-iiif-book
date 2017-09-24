<template>
  <div id="app">
    <header>
      <span>IIIF Vue Components</span>
    </header>
    <main>
      <tree class="sidebar" v-bind:toc="manifestation.getVueTree()"></tree>
      <thumbnails class="content" v-bind:thumbnails="manifestation.photos()"></thumbnails>
    </main>
  </div>
</template>

<script>
import {mixins, Tree, Thumbnails} from 'manifestation-vue'
import manifest from './data/manifest'
import manifesto from '../node_modules/manifesto.js/dist/server/manifesto.js'
const manifestation = Object.assign(manifesto.create(JSON.stringify(manifest)), mixins)

export default {
  name: 'app',
  components: {
    Tree,
    Thumbnails
  },
  data() {
    return {
      manifestation: manifestation
    }
  },
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  text-align: left;
  margin: 40px;
}

header {
  margin: 0;
  height: 56px;
  padding: 0 16px 0 24px;
  background-color: #35495E;
  color: #ffffff;
}

header span {
  display: block;
  position: relative;
  font-size: 20px;
  line-height: 1;
  letter-spacing: .02em;
  font-weight: 400;
  box-sizing: border-box;
  padding-top: 16px;
}

.sidebar {
  width: 300px;
  float: left;
}
.content {
  margin-left: 300px;
}
.clear {
  clear: both;
}

</style>
