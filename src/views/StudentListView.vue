<script setup lang="ts">
import type { StudentItem } from '@/type'
import { ref, type Ref } from 'vue'
import StudentService from '@/services/StudentService';
import StudentCard from '@/components/StudentCard.vue';

const students: Ref<Array<StudentItem>> = ref([])

StudentService.getEvent().then((response) => {
  students.value = response.data
  console.log(students.value)
})
</script>

<template>
  <h1 class="mt-6 mb-6 font-bold text-2xl bg-green-300">Events For Good</h1>
  <main class="flex flex-col items-center">
    <StudentCard v-for="student in students" :key="student.id" :student="student"></StudentCard>
  </main>
</template>

<style scoped>
</style>