<template>
    <div id="movie-filter">
        <h2>Filter results</h2>

        <h3>By time of day</h3>
        <div class="filter-group">
            <check-filter category="time" v-for="time in times" v-bind:title="time" v-on:check-filter="checkFilter"></check-filter>
        </div>
        <h3>By genre</h3>
        <div class="filter-group">
            <check-filter category="genre" v-for="genre in genres" v-bind:title="genre" v-on:check-filter="checkFilter"></check-filter>
        </div>
    </div>
</template>
<script>
    import CheckFilter from './CheckFilter.vue';
    import genres from '../util/genres';
    import times from '../util/times';

    export default{
        data: function () {
            return {
                genres,
                times
            }
        },
        methods: {
            checkFilter: function (category, title, checked) {
                this.$emit('check-filter', category, title, checked);
            }
        },
        components: {
            CheckFilter
        }
    }
</script>