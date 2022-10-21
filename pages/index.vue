<template>
    <div v-if="tweets" v-for="tweet in tweets.data" :key="tweet.id" class="card bg-base-100 shadow-xl mb-3">
        <div class="card-body">
            <div class="flex flex-row">
                <div>
                    <div class="avatar">
                        <div class="w-16 rounded-full">
                            <img :src="tweet.user.profile.image" />
                        </div>
                    </div>
                </div>
                <div class="ml-3">
                    <b>{{tweet.user.name}}</b>&nbsp;&nbsp;
                    <span class="text-zinc-400">@{{tweet.user.username}}</span>
                    <p>{{tweet.content}}</p>
                    
                </div>
            </div>
            <div class="card-actions justify-end">
            <button class="btn btn-primary">Buy Now</button>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
    export default {
        created(){
            axios.get('http://localhost:8000/api/tweets').then(response => {
                console.log(response);
                this.tweets = response.data;
            })
        },
        data(){
            return {
                tweets: null
            }
        }
    }
</script>