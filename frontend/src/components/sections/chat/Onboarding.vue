<template>
    <div class="fixed z-10 inset-0 overflow-y-auto" aria-labelledby="modal-title" role="dialog" aria-modal="true">
        <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
            <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" aria-hidden="true"></div>
            <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
            <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full">
                <OnboardingNationality v-if="!onboarding.registered && onboarding.showNationality"  @nextStep="onboarding.next"/>
                <OnboardingGender v-if="!onboarding.registered && onboarding.showGender"  @nextStep="onboarding.next" />
                <OnboardingAge v-if="!onboarding.registered && onboarding.showAge"  @nextStep="onboarding.next" />
                <OnboardingSuccess v-if="onboarding.registered || onboarding.showSuccess" @register="onboarding.registerUser"/>
            </div>
        </div>
    </div>
</template>

<script setup>
import { useOnboardingStore } from '@/stores/onboarding/index'

const onboarding = useOnboardingStore()
onboarding.checkVisitor()

</script>

