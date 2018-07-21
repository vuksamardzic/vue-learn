<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <h2 v-text="mainTitle"></h2>
        </div>
        <div class="col-auto">
          <img src="./assets/logo.png" :alt="desc">
        </div>
        <div class="col-auto">
          <p class="mb-0">Free to use</p>
          <span class="text-info small py-2" v-if="stars >= 10">Very popular</span>
          <span class="text-info small py-2" v-else-if="stars > 0 && stars < 10">Popular</span>
          <span class="text-info small py-2" v-else>Not so popular</span>
          <ul>
            <li v-for="(i, key) in details"
                @mouseover="setOverKey(key)"
                :class="{'text-info': overKey === key}"
                :key="key">{{ i }}
            </li>
          </ul>
          <div class="row">
            <div class="col-12">
              <button class="btn btn-primary"
                      @click="onStarIncrement">Give a star
              </button>
              <span class="pl-2 border-light">stars: ({{ stars }})</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import 'bootstrap/dist/css/bootstrap.min.css';

  export default {
    name: 'app',
    data() {
      return {
        mainTitle: 'vue.js',
        desc: 'vue.js logo',
        details: [
          'fast',
          'light',
          'elegant'
        ],
        overKey: undefined,
        stars: 0
      };
    },
    methods: {
      onStarIncrement() {
        this.stars += 1;
      },
      setOverKey(key) {
        this.overKey = key;
      }
    },
    components: {}
  };
</script>
