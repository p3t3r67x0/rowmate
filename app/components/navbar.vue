<template>
<div v-click-outside="hideNav" class="fixed z-50 w-full bg-color-nav mb-3 lg:mb-8 lg:px-6">
  <header class="flex flex-wrap items-center">
    <div class="flex-1 flex justify-between items-center py-2 pl-3 lg:pl-0">
      <nuxt-link :to="localePath('/')" class="flex justify-between focus:outline-none text-lg font-bold">
        <span class="text-2xl text-color-nav font-light">rowmate.org</span>
      </nuxt-link>
    </div>

    <label @click="toggleNav" class="cursor-pointer lg:hidden block py-2 pr-4">
      <svg class="w-5 h-5 text-color-nav focus:outline-none fill-current" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
        <title>Menu</title>
        <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"></path>
      </svg>
    </label>

    <div :class="[showNav ? 'block z-50' : 'hidden']" class="w-full border-t lg:border-0 border-gray-800 mt-2 lg:mt-0 lg:flex lg:items-center lg:w-auto">
      <ul class="lg:flex items-center justify-between text-base text-color-nav pt-0 lg:pt-0">
        <li @click="toggleNav" class="border-b lg:border-b-2 border-gray-800 lg:border-transparent lg:hover:border-white">
          <nuxt-link :to="localePath('/signin')" class="block py-3 px-3 lg:p-4 focus:outline-none hover:bg-gray-800 lg:hover:bg-transparent">{{ $t('signin') }}</nuxt-link>
        </li>
        <li @click="toggleNav" class="border-b lg:border-b-2 border-gray-800 lg:border-transparent lg:hover:border-white">
          <nuxt-link :to="localePath('/signup')" class="block py-3 px-3 lg:p-4 focus:outline-none hover:bg-gray-800 lg:hover:bg-transparent">{{ $t('signup') }}</nuxt-link>
        </li>
      </ul>
    </div>
  </header>
</div>
</template>

<script>
export default {
  data() {
    return {
      showNav: false,
      showDropdown: false
    }
  },
  computed: {
    availableLocales() {
      return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
    }
  },
  methods: {
    hideNav() {
      return this.showNav = false
    },
    hideDropdown() {
      return this.showDropdown = false
    },
    toggleNav() {
      return this.showNav = !this.showNav
    },
    toggleDropdown() {
      this.toggleNav()
      return this.showDropdown = !this.showDropdown
    },
  }
}
</script>
