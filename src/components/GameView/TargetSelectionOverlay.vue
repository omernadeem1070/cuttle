<template>
  <div id="player-hand-targeting" class="d-flex justify-start" :class="{ 'my-turn': isPlayersTurn }">
    <game-card :suit="selectedCard.suit" :rank="selectedCard.rank" :is-selected="true" @click="$emit('cancel')" />
    <div id="target-selection-header-wrapper" class="d-flex flex-column align-center">
      <h2>Choose {{ moveDisplayName }} Target</h2>
      <v-btn variant="outlined" color="primary" class="mt-2" data-cy="cancel-target" @click="$emit('cancel')">
        Cancel
      </v-btn>
    </div>
    <v-btn icon data-cy="cancel-target-mobile" @click="$emit('cancel')">
      <v-icon icon="mdi-close" size="x-large" />
    </v-btn>
  </div>
</template>

<script>
import GameCard from '@/components/GameView/GameCard.vue';

export default {
  name: 'TargetSelectionOverlay',
  components: {
    GameCard,
  },
  emits: ['cancel'],
  props: {
    selectedCard: {
      type: Object,
      required: true,
    },
    isPlayersTurn: {
      type: Boolean,
      required: true,
    },
    moveDisplayName: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped lang="scss">
#player-hand-targeting {
  padding: 12px;
}
#target-selection-header-wrapper {
  width: 100%;
}
</style>
