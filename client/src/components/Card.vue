<template>
    <b-card
        :bg-variant="isBlackCard ? 'dark' : 'default'"
        :text-variant="isBlackCard ? 'white' : ''"
        class="player-card"
        :class="{canSelect, isBlackCard}"
        @click="handleClick"
    >
        <b-card-text>
            {{ getText() }}
        </b-card-text>
    </b-card>
</template>

<script>
    export default {
        props: {
            created_at: String,
            id: String,
            nsfw: Boolean,
            text: Array,
            isBlackCard: Boolean,
            canSelect: Boolean,
        },
        computed: {
            variant() {
                return this.isBlackCard ? "dark" : "default";
            }
        },
        methods: {
            getText() {
                return this.text.join("_____");
            },
            handleClick() {
                if (this.canSelect) {
                    this.$emit('clicked', this.$vnode.key);
                }
            },
        }
    }
</script>

<style scoped>
    .player-card {
        overflow-wrap: break-word;
        word-wrap: break-word;
        word-break: break-word;

        -webkit-hyphens: auto;
        -webkit-hyphenate-limit-before: 3;
        -webkit-hyphenate-limit-after: 3;
        -webkit-hyphenate-limit-chars: 6 3 3;
        -webkit-hyphenate-limit-lines: 2;
        -webkit-hyphenate-limit-last: always;
        -webkit-hyphenate-limit-zone: 8%;
        -moz-hyphens: auto;
        -moz-hyphenate-limit-chars: 6 3 3;
        -moz-hyphenate-limit-lines: 2;
        -moz-hyphenate-limit-last: always;
        -moz-hyphenate-limit-zone: 8%;
        -ms-hyphens: auto;
        -ms-hyphenate-limit-chars: 6 3 3;
        -ms-hyphenate-limit-lines: 2;
        -ms-hyphenate-limit-last: always;
        -ms-hyphenate-limit-zone: 8%;
        hyphens: auto;
        hyphenate-limit-chars: 6 3 3;
        hyphenate-limit-lines: 2;
        hyphenate-limit-last: always;
        hyphenate-limit-zone: 8%;

        max-width: 10rem;
        min-height: 14rem;

        margin: auto;
        width: 50%;
    }

    .canSelect {
        cursor: pointer;
    }

    .isBlackCard {
        cursor: default;
    }
</style>