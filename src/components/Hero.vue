<template>
  <header class="hero">
    <v-carousel
      cycle
      height="100vh"
      hide-delimiter-background
      :show-arrows="false"
    >
      <v-carousel-item
        v-for="(slide, i) in slides"
        :key="i"
      >
        <v-img
          height="100vh"
          :src="imagePath(slide.sm)"
          :srcset="`${imagePath(slide.sm)} 640w,
                  ${imagePath(slide.md)} 1280w,
                  ${imagePath(slide.lg)} 1920w`"
          >
          <v-overlay class="overlay" :absolute="true">
            <v-container>
              <v-row class="spacing align-center flex-column">
                <h1 class="text-h3 text-md-h2 font-weight-bold text-center mb-3">
                  {{ slide.title }}
                </h1>
                <h4 class="subtitle-2 text-md-subtitle-1 text-center mb-9">
                  {{ slide.text }}
                </h4>
                <v-btn
                  large
                  elevation="4"
                  color="light-green darken-4"
                  :to="{ name: slide.to }"
                >
                  Conocé más
                </v-btn>
              </v-row>
            </v-container>
          </v-overlay>
        </v-img>
      </v-carousel-item>
    </v-carousel>
  </header>
</template>

<script>
import imageMixin from '@/mixins/images'

export default {
  name: 'hero',
  mixins: [imageMixin],
  data () {
    return {
      slides: [
        {
          sm: '/portada-1-640w-min.jpg',
          md: '/portada-1-1280w-min.jpg',
          lg: '/portada-1-1920w-min.jpg',
          title: 'Diseñamos tu jardín',
          text: 'Todo jardín empieza con una historia de amor. Antes de que cualquier árbol sea plantado o un estanque construido, es necesario que ellos hayan nacido dentro del alma.',
          to: 'etapas'
        },
        {
          sm: '/portada-2-640w-min.jpg',
          md: '/portada-2-1280w-min.jpg',
          lg: '/portada-2-1920w-min.jpg',
          title: 'Creamos tu entorno verde',
          text: 'Quien no planta un jardín en su interior, no planta jardines en el exterior y tampoco pasea por ellos.',
          to: 'diseniadoras'
        },
        {
          sm: '/portada-3-640w-min.jpg',
          md: '/portada-3-1280w-min.jpg',
          lg: '/portada-3-1920w-min.jpg',
          title: 'Remodelamos tu jardín',
          text: 'Reinventamos tu espacio conectándolo con la naturaleza, donde las dimensiones no importan, donde el protagonista sos vos. Viví la experiencia natural con los cinco sentidos.',
          to: 'proyectos'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  .hero h4 {
    max-width: 50vw;
  }

  @media only screen and (max-width: 900px) {
    .hero h4 {
      max-width: 75vw;
    }
  }
</style>
