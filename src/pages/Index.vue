<template>
  <q-page class="flex flex-center">
    <div>
    <q-btn color="primary" label="Get Picture" @click="captureImage" />

    <img :src="imageSrc">
  </div>
  </q-page>
</template>

<style>
</style>

<script>
document.addEventListener('deviceready', () => {
  // it's only now that we are sure
  // the event has triggered
}, false)
export default {
  name: 'PageIndex',
  data () {
    return {
      imageSrc: ''
    }
  },
  methods: {
    captureImage () {
      navigator.camera.getPicture(
        data => { // on success
          this.imageSrc = `data:image/jpeg;base64,${data}`
        },
        () => { // on fail
          this.$q.notify('Could not access device camera.')
        },
        {
          // camera options
        }
      )
    }
  }
}
</script>
