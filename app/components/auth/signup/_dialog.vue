<template lang="pug">
  v-dialog(
    lazy
    v-model="model"
    :max-width="600"
    :persistent="$get(form, 'loading')"
    no-click-animation
    contentClass="bradius-a")
    slot
</template>

<script>
import {
  getState,
  getMethods
} from '@/storeInterface'

export default {
  computed: {
    ...getState('auth'),
    model: {
      get () {
        return this.$get(this.form, 'name') === 'signup'
      },
      set (value) {
        this.setForm(value ? { name: 'signup'} : null)
      }
    }
  },
  methods: {
    ...getMethods('auth'),
  }
}
</script>
