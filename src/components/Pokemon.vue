<template>
    <div>
        <transition name="fade">
            <Modal 
            v-if="show"
            :onClose="onClose"
            :pokemon="pokemon"
            />
        </transition>
            <li @click="handleClick" :style=" { background: pokemon.color_1 }">
                <img v-bind:src="pokemon.url_image">
                <h3>{{pokemon.pokemon}}</h3>
            </li>
    </div>
</template>

<script>
import Modal from './Modal';

function wait(ms){
   var start = new Date().getTime();
   var end = start;
   while(end < start + ms) {
     end = new Date().getTime();
  }
}

export default {
    data() {
        return {
            show: false
        }
    },
    props: {
        pokemon: Object,
    },
    methods: {
        handleClick() {
            this.show = true;
        },
        onClose() {
            this.show = false;
        },
        dance() {
            this.dance = true;
            wait(3000);
            this.dance = false;
        }
    },
    components: {
        Modal
    }
}
</script>

<style scoped>
    img {
        width: 100%;
    }
    li {
        border: 2px solid navy;
        margin: 5px;
        padding: 1vw;
        width: 200px;
        display: flex;
        flex-direction: column;
        text-align: center;
        border-radius: 10px;
        box-shadow: 2px 2px 2px;
    }
    li:hover {
        border-color: orange;
        box-shadow: 8px 8px 8px;
    }
    h3 {
        background-color: antiquewhite;
        border: 4px outset gray;
    }
    .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
    }
    .fade-enter, .fade-leave-to{
    opacity: 0;
    }
</style>
