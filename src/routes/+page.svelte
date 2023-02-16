<script lang="ts">
	import { Capacitor } from '@capacitor/core';

	import { SignInWithApple } from '@changenode/capacitor-sign-in-with-apple';

	let device: any;
	let r: any;
	let e: any;

	async function auth() {
		device = Capacitor.getPlatform();

		SignInWithApple.auth()
			.then((response: any) => {
				console.log(response);
				r = response;
			})
			.catch((response: any) => {
				console.error(response);
				e = response;
			});
	}

	auth();
</script>

<h1>Fancy App</h1>
<p>This is pretty darn fancy.</p>
<button on:click={auth}>Sign In With Apple</button>
<textarea bind:value={r} />
<textarea bind:value={e} />

<style>
    button {display: block; width: 100%;}
    textarea {display: block; width: 100%;}
</style>
