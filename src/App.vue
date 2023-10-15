<!-- <template>
    <Repl
    :editor="Monaco"
    theme="light"
    :show-compile-output="true"
    :auto-resize="true"
    :clear-console="false"
    @keydown.ctrl.s.prevent
    @keydown.meta.s.prevent
  />
</template>

<script setup lang="ts">
import { Repl } from '@vue/repl'
import Monaco from '@vue/repl/monaco-editor'
</script>

<style scoped></style> -->

<script setup lang="ts">
import { Repl } from "@vue/repl";
import Monaco from "@vue/repl/monaco-editor";
import { ReplStore } from './utils/store'
import { watchEffect } from "vue";

const store = new ReplStore({
  serializedState: location.hash.slice(1),
})

watchEffect(() => history.replaceState({}, '', store.serialize()))
</script>

<template>
  <div class="container">
    <Repl class="container" :editor="Monaco" :store="store" :clear-console="false" @keydown.ctrl.s.prevent @keydown.meta.s.prevent />
  </div>
</template>

<style scoped>
.container {
  height: 100vh;
}
</style>
