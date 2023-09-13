<script setup>
    import MainNav from '@/Components/MainNav.vue'
    // import LogoIcon from '@/Components/icons/LogoIcon.vue';
    import NavSection from '@/Components/NavSection.vue';
    import { ref } from 'vue';

    const isCollapsed = ref(false)

    function collapseSidebar() {
        isCollapsed.value = !isCollapsed.value;
    }
</script>

<template>

<div class="flex items-start min-h-screen">
    <div class="sticky top-0 z-10 min-h-screen duration-300 bg-indigo-600" :class="[ !isCollapsed ? 'w-64' : 'w-16']">
        <div class="relative p-4">
            <button class="absolute -right-8" @click="collapseSidebar">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-[18px] h-[18px]" :class="{ 'rotate-180' : isCollapsed }">
                <path stroke-linecap="round" stroke-linejoin="round" d="M18.75 19.5l-7.5-7.5 7.5-7.5m-6 15L5.25 12l7.5-7.5" />
                </svg>

            </button>
            <div id="branding" class="flex" :class="[ isCollapsed ? 'justify-center' : 'items-center space-x-2']">
                <span class="text-2xl text-gray-50"><i class="fa-brands fa-laravel"></i></span>
                <h1 v-show="!isCollapsed" class="text-xl font-semibold text-gray-50">Laravel Inertia</h1>
            </div>

            <span class="text-[10px] font-extrabold text-gray-300 uppercase">Menu</span>

            <!-- <ul>
                <li></li>
            </ul> -->
            <!-- <hr class="border-gray-600"> -->
            <NavSection :hidden="isCollapsed" />
        </div>
    </div>
    <div class="flex-1 min-h-screen">
        <slot />
    </div>
</div>

</template>
