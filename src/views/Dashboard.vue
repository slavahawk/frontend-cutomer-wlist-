<script setup lang="ts">
import CardWine from "@/components/Wine/CardWine.vue";
import { useWineStore } from "@/stores/useWineStore.ts";
import { storeToRefs } from "pinia";

const { getWines, clearData } = useWineStore();
const { wines, isLoad } = storeToRefs(useWineStore());
</script>

<template>
  <div class="mb-4 flex gap-2">
    <Button :loading="isLoad" label="Получить вина" @click="getWines" />
    <Button label="Очистить" @click="clearData" />
  </div>
  <div
    v-if="wines.length"
    class="grid grid-cols-[repeat(auto-fit,minmax(292px,1fr))] gap-4"
  >
    <CardWine v-for="wine in wines" :key="wine.id" :wine="wine" />
  </div>
</template>
