<script setup lang="ts">
import { getWalletState, initTomoModal } from '@tomo-inc/tomo-web-sdk'
import '@tomo-inc/tomo-web-sdk/style.css'

import { onMounted } from 'vue'

const tomoModal = () => {
  try {
    initTomoModal({
      theme: 'light',
      clientId:
        'izEkhMZuzamb07eI3Vv7lscUK6BmoOG6xtOKFuodirUl6xuL57PPl0TolUBIzJN5fpgBsmtMpSpwQ0krBEtE71Bm',
      chainTypes: ['evm'],
      onConnect: () => {
        const walletState = getWalletState()
        console.log('onConnect', walletState)
      },
    })
  } catch (error) {
    console.log(error, 'initTomoModal')
  }
}

const openModal = () => {
  window.openTomoConnectModal?.()
}

onMounted(() => {
  tomoModal()
})
</script>

<template>
  <main>
    <div class="text-div" @click="openModal()">@tomo-inc/tomo-web-sdk</div>
  </main>
</template>

<style lang="css">
.text-div {
  font-size: 30px;
  color: #fff;
  cursor: pointer;
}
</style>
