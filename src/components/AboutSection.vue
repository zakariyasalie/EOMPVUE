<template>
    <div class="container">
        <div class="row justify-content-center">
            <img src="https://codjoelmayer.github.io/projectImages/images/joel9.jpg" alt="profile"
                class="img-fluid shadow rounded-top" loading="lazy">
        </div>
        <div class="row justify-content-center">
            <div v-if="about?.length">
                <p class="lead" v-for="(self, index ) in about" :key="index">
                    {{ self }}
                </p>
            </div>
            <Spinner v-else />
        </div>
    </div>
</template>

<script setup>
import Spinner from './Spinner.vue'
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'
const store = useStore()
const about =
    computed(() => store.state.about)

onMounted(() => {
    store.dispatch('fetchAbout')
})

</script>
