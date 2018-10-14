<!-- Contains the abilities user can use. -->
<template>
    <div class="controls text-center" :class="color">
        <h1 v-if="questionFeedback">{{ this.questionFeedback }}</h1>
        <section class="row">
                <button id="attack" @click="onNextQuestion('attack')">ATTACK</button>
                <button id="special-attack" @click="onNextQuestion('special-attack')">SPECIAL ATTACK</button>
                <button id="heal" @click="onNextQuestion('heal')">HEAL</button>
                <button id="give-up" @click="onNextQuestion('give-up')">GIVE UP</button>
        </section>
    </div>
</template>
<script>
export default {
  data() {
    return {
      color: "white",
      questionStatus: true
    };
  },
  methods: {
    // Forwards the chosen ability
    onNextQuestion(action) {
      this.$emit("confirmed", action);
    },
    // Changes background whether answer was false/correct.
    backgroundColorChanger() {
      if (this.questionFeedback == "False!") {
        this.color = "red";
      } else {
        this.color = "green";
      }
    }
  },
  created() {
    this.backgroundColorChanger();
  },
  props: ["questionFeedback"]
};
</script>
<style scoped>
.green {
  background-color: rgb(127, 241, 127);
}

.red {
  background-color: rgb(233, 86, 86);
}
.white {
  background-color: rgb(255, 255, 255);
}
</style>

