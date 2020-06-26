<template>
  <div id="app">
    <p class="my-3">
      カード操作による選択結果： {{ status }}
    </p>
    <GameCardsStack
      :cards="visibleCards"
      @cardAccepted="handleCardAccepted"
      @cardRejected="handleCardRejected"
      @cardSkipped="handleCardSkipped"
      @hideCard="removeCardFromDeck"
    />
  </div>
</template>

<script>
import GameCardsStack from '~/components/GameCardsStack';

export default {
  name: 'App',
  components: {
    GameCardsStack,
  },

  data() {
    return {
      status: '',
      visibleCards: ['Test', 'Vue.js', 'Webpack'],
    };
  },

  methods: {
    handleCardAccepted() {
      this.status = '同意する';
    },
    handleCardRejected() {
      this.status = '拒否する';
    },
    handleCardSkipped() {
      this.status = 'スキップ';
    },
    removeCardFromDeck() {
      this.visibleCards.shift();
    },
  },
};
</script>

<style lang="scss">
@import 'assets/styles/mixins.scss';

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
}
</style>
