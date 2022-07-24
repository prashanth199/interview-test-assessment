<script setup>
import Data1 from "@/Data/drug1.json";

console.log(Data1.fields.sort((a,b)=>{
    return a.order - b.order;
}));
</script>

<template>
    <div v-for="data in Data1.fields.sort((a,b)=>{a.order-b.order})" :key="data.key">
        <label>{{data.label}}</label>
        <input v-if="data.type === 'text'||data.type==='date'" :type="data.type" :required="data.isRequired" :readonly="data.isReadonly">
        <input v-if="data.type === 'number'" type="number" :required="data.isRequired" :readonly="data.isReadonly"/>
        <p v-if="data.type==='number'">Unit {{data.unit}}</p>
        <select v-if="data.type==='dropdown'" name="" id="" :required="data.isRequired" :readonly="data.isReadonly">
            <option v-for="item in data.items"  :value="item.value">{{item.text}}</option>
        </select>
    </div>
</template>