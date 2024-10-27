<script setup lang="ts">
import EventCard from '@/components/EventCard.vue';
import EventCategoriesAndOrganizer from '@/components/EventCategoriesAndOrganizer.vue';
import type { Event } from '@/type.ts';
import { ref } from 'vue';

const events = ref<Event[]>([
  {
    id: 5928101,
    category: 'animal welfare',
    title: 'Cat Adoption Day',
    description: 'Find your new feline friend at this event.',
    location: 'Meow Town',
    date: 'January 28, 2022',
    time: '12:00',
    petsAllowed: true,
    organizer: 'Kat Laydee'
  },
  {
    id: 4582797,
    category: 'food',
    title: 'Community Gardening',
    description: 'Join us as we tend to the community edible plants.',
    location: 'Flora City',
    date: 'March 14, 2022',
    time: '10:00',
    petsAllowed: true,
    organizer: 'Fern Pollin'
  },
  {
    id: 8419988,
    category: 'sustainability',
    title: 'Beach Cleanup',
    description: 'Help pick up trash along the shore.',
    location: 'Playa Del Carmen',
    date: 'July 22, 2022',
    time: '11:00',
    petsAllowed: false,
    organizer: 'Carey Wales'
  }
]);
</script>

<template>
  
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    <div class="event-card">
      <EventCategoriesAndOrganizer
      :organizer-name="event.organizer"
      :categories="[event.category]"
      v-for="event in events"
      :key="`${event.id}-info`"
    /></div>
   
    />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}

/* 为了让分类和组织者信息对齐 */
.event-categories-and-organizer {
  text-align: right;
  width: 100%;
}

.event-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
  box-sizing: border-box; /* 确保边框和内边距包含在总宽度和高度内 */
}

.event-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}

.event-categories-and-organizer {
  display: flex;
  justify-content: flex-end;
  font-size: 16px; /* 调整字体大小以匹配需求 */
  margin-top: 10px; /* 与事件卡片之间的间距 */
}

.text-align-right {
  margin-left: 10px; /* 可以调整间距 */
}
</style>