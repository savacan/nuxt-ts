<template>
  <div>
    <h1>{{ title }}</h1>
    <div>
      <p>{{ `counter: ${data.count}` }}</p>
      <button type="button" @click="onIncrement">increment</button>
      <button type="button" @click="onDecrement">decrement</button>
    </div>
    <div>
      <p>{{ content }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from '@vue/composition-api'

type Props = {
  title: string
  content: string
}

type Data = {
  count: number
}

export default defineComponent<Props>({
  props: {
    title: {
      type: String,
    },
    content: {
      type: String
    }
  },
  setup(props: Props) {
    const data = reactive<Data>({ count: 0 })
    const onIncrement = (): void => {
      data.count += 1
    }
    const onDecrement = (): void => {
      data.count -= 1
    }
    return {
      data,
      title: props.title,
      onIncrement,
      onDecrement,
    }
  },
})
</script>

<style></style>
