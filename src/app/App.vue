<template>

        <div class="container">
            <div class="row">
                <div class="col-sm-6 offset-sm-3">
                    <div class="card card-login mt-5">
                        <div class="card-body">
                    <div v-if="alert.message" :class="`alert ${alert.type}`">{{alert.message}}</div>
                    <router-view></router-view>
                </div>
            </div>
        </div>
            </div>
        </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
    name: 'app',
    computed: {
        ...mapState({
            alert: state => state.alert
        })
    },
    methods: {
        ...mapActions({
            clearAlert: 'alert/clear' 
        })
    },
    watch: {
        $route (to, from){
            // clear alert on location change
            this.clearAlert();
        }
    } 
};
</script>
<style>
body{
   font-family: "Poppins", sans-serif;
  height: 100vh;
}

.card-login{
    border: 0;
    border-radius: 2rem;
    box-shadow: 0 0.5rem 1rem 0 rgba(0, 0, 0, 1)
}

</style>