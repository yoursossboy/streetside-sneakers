<script setup>
import Card from './Card.vue'

defineProps({
    items: Array,
    isFavorites: Boolean
})

const emit = defineEmits(['addToFavorite', 'addToCart'])
</script>

<template>
    <div class="grid grid-cols-4 gap-5 mb-5" v-auto-animate>
        <Card v-for="item in items"
            :key="item.id"
            :id="item.id"
            :title="item.title"
            :imageUrl="item.imageUrl"
            :price="item.price"
            :OnClickFavorite="isFavorites ? null : () => emit('addToFavorite', item)"
            :OnClickAdd="isFavorites ? null : () => emit('addToCart', item)"
            :isFavorite="item.isFavorite"
            :isAdded="item.isAdded"
        />
    </div>
</template>