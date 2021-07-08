<template>
	<div class="slider">
		<template v-if="images.length > 1">
			<div id="slider" class="relative">
				<ImageBlock :item="images[activeImage]" :title="title" />
				<div class="grid absolute top-0 left-2 h-full z-20">
					<button
						class="self-center px-3 py-1 font-bold border-none shadow-sm bg-white font-bold text-2xl rounded-md"
						@click="$changeImg(1)"
					>
						&lsaquo;
					</button>
				</div>
				<div class="grid absolute top-0 right-2 h-full z-20">
					<button
						class="self-center px-3 py-1 font-bold border-none shadow-sm bg-white font-bold text-2xl rounded-md"
						@click="$changeImg(2)"
					>
						&rsaquo;
					</button>
				</div>
			</div>
		</template>
		<template v-else>
			<ImageBlock :item="images[0]" :title="title" />
		</template>
	</div>
</template>

<script>
	import ImageBlock from "@/components/img.vue";
	export default {
		components: {
			ImageBlock
		},
		props: {
			images: {
				type: Array,
				default: null
			},
			title: {
				type: String,
				default: "Dataline Sport"
			}
		},
		data(){
			this.length = this.props.images.length;
			if(length > 1)
				setInterval(() => {
					this.$changeImg(1);
				}, 3000);
		},
		mounted(){
			if(length > 1)
				setInterval(() => {
					this.$changeImg(1);
				}, 3000);
		},
		changeImg (e) {
			console.log(e)
			if(this.length == 0) this.length = this.props.images.length;
			if (e == 1) {
				if (this.activeImage == 0) this.activeImage = this.length - 1;
				else this.activeImage -= 1;
			} else {
				if (this.length == this.activeImage + 1) this.activeImage = 0;
				else this.activeImage += 1;
			}
			return {
				image: this.images[this.activeImage]
			}
		}
	}
</script>
