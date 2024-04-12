<template>
  <div>

  </div>
</template>

<script setup lang="ts">
const page = ref(1);

// cached data has no typing/any
const { data: iLooseTyping } = await useAsyncData(
  'posts',
  async () => "hello",
  {
    watch: [page],
    getCachedData(key, nuxtApp) {
			return nuxtApp.payload.data[key] || nuxtApp.static.data[key] 
		},
  }
);

// No cached data has typing
const { data: iAmTyped } = await useAsyncData(
  'posts',
  async () => "hello",
  {
    watch: [page],
  }
);
</script>
