<script setup>
import { reactive, computed, ref } from 'vue';

const author = reactive({
    name: 'John Doe',
    books: [
        'Vue 2 - Advanced Guide',
        'Vue 3 - Basic Guide',
        'Vue 4 - The Mystery'
    ]
});
const dynmicId = reactive({
    name:'ddddd',
})

const publishedBooksMessage = computed(() => {  
    return author.books.length > 0 ? 'Yes' : 'No'
})

const isButtonDisabled = reactive({
    disabled:false,
    number:4,
    seen: true
})

const handle = () => {
    isButtonDisabled.number ++;
    console.log(document.getElementById('span'))

    
}
let state =     reactive({
    count:0 
})
let n = state.count
    n++
let   {count} = state
count++
 function printf (){
    console.log(state.count);//失去了响应式连接，值不想同   
    console.log(count);
 }
 printf()
 const firstname = ref('stphen')
 const lastname = ref('curry')
 const fullname = computed({
    get(){
        return firstname.value + ' ' + lastname.value
    },
    set(newValue){
        [firstname.value,lastname.value] = newValue.split('')
    }
 })

</script>


  

<template>
    <!-- <p>Has published books:</p>
    <span>{{ publishedBooksMessage }}</span> -->
    <span>{{dynmicId.name}}</span>
    <input type="text" v-bind:value="dynmicId.name">
    <!-- 通过控制isButtonDisabled.disabled的布尔值来控制页面上的按钮和复选框的状态 -->
    <button :disabled=[isButtonDisabled.disabled]>nihao</button>
    <input type="checkbox" :disabled="isButtonDisabled.disabled">
    <span id="span">绑定：{{ isButtonDisabled.number + 1}}</span>
    <button @click="handle">+1</button>
    <!-- 指令 -->
    <div v-if="isButtonDisabled.seen">是否显示</div>
    <h2>firstname:{{firstname}}</h2>
    <h2>lastname:{{ lastname }}</h2>
    <h2>fullname:{{fullname}}</h2>



</template>

<style scoped>
header {
    line-height: 1.5;
}
</style>
