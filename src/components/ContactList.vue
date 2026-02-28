<script>
export default {
  props: {
    contacts: {
      type: Array,
      default: () => [],
    },

    activeIndex: {
      type: Number,
      default: -1,
    },
  },

  emits: ["update:activeIndex"],

  methods: {
    updateActiveIndex(index) {
      this.$emit("update:activeIndex", index);
    },
  },
};
</script>

<template>
  <ul class="list-group">
    <li
      v-for="(contact, index) in contacts"
      :key="contact._id"
      class="list-group-item"
      :class="{ active: index === activeIndex }"
      @click="updateActiveIndex(index)"
    >
      {{ contact.name }}
    </li>
  </ul>
</template>