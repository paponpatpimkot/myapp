<template>
    <div>
        <img :src="picture" :width="size" :height="size"><br>
        <form @submit.prevent="submitForm">
            <label for=""></label>
            <input type="text" @input="setNickName" refs="nicknameEL">
            <button type="submit">บันทึก</button>
        </form>
        <p>ชื่อ : {{ firstname }}</p>
        <p>นามสกุล : {{ lastname }}</p>
        <p>ชื่อเล่น : {{ nickname }}</p>
        <p>อายุ : {{ age }}</p>
        <p>ที่อยู่ : <span v-html="address"></span></p>
        <p>งานอดิเรก :</p>
            <ul>
                <li>{{ hobby[0] }}</li>
                <li>{{ hobby[1] }}</li>
                <li>{{ hobby[2] }}</li>
            </ul>
        <p>ข้อมูลพื้นฐาน : </p>
            <ul>
                <li>เพศ : {{ general.gender }}</li>
                <li>น้ำหนัก : {{ general.weight }}</li>
                <li>ส่วนสูง : {{ general.height }}</li>
                <li>โรคประจำตัว : {{ general.status }}</li>
            </ul>
            <button @click="showData">คลิกเพื่อดูข้อมูล</button>
            <button @click="increment(10)">เพิ่มค่า</button>
            <button @click="decrement(3)">ลดค่า</button>
    </div>
</template>
<script>
import { defineSSRCustomElement } from 'vue'

   export default {
    data(){
        return{
            firstname: "Myname",
            lastname: "MyLastname",
            nickname: "",
            age: 25,
            address: "<i>Chonburi</i>",
            picture: "https://cdn-icons-png.flaticon.com/512/8288/8288361.png",
            size: 150,
            hobby : ["ทำสวน","เล่นเกม","ดูหนัง"],
            general : {gender:"ชาย",weight:63.5,height:173.5,status:false}
        }
    },
    methods:{
        getFullnaem(){
            return `$(this.firstname) $(this.lastname)`
        },
        showData(){
            alert(this.firstname)
        },
        increment(value){
            this.age += value
        },
        decrement(value){
            this.age -= value
        },
        setNickName(event){
            this.nickname=event.target.value
        },
        submitForm(){
            alert('บันทึกข้อมูลเรียบร้อย')
        }
    }
   }
</script>


