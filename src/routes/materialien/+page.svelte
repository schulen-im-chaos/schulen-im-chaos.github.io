<script lang="ts">
	import Notice from './Notice.svelte';
	import db from '$lib/data.json';
</script>

<svelte:head>
	<title>Lernmaterialien</title>
	<meta name="description" content="Lernmatierialien" />
</svelte:head>

<h2 class="h2">Lernmaterialien</h2>

<Notice />

<div class="grid md:grid-cols-3 2xl:grid-cols-6 gap-6">
	{#each db.levels as level}
		<a href="/materialien/{level.name}" class="card w-fit bg-initial card-hover overflow-hidden">
			<header>
				<img
					src="/img/levels/{level.name}.jpg"
					alt="{level.name} Symbolbild"
					class="bg-black/50 w-full"
				/>
			</header>
			<div class="p-4 space-y-4 text-xl font-bold">{level.name}</div>
		</a>
	{:else}
		<aside class="alert variant-filled-warning !m-0">
			<!-- Icon -->
			<div><i class="fa-solid fa-triangle-exclamation"></i></div>
			<!-- Message -->
			<div class="alert-message">
				<h3 class="h3">Noch keine Lernmaterialien!</h3>
				<p>
					Warte bis welche hinzugefügt werden oder füge selber <a
						class="anchor"
						href="/materialien/beitragen"
						data-sveltekit-preload-data="hover">welche</a
					>! hinzu!
				</p>
			</div>
		</aside>
	{/each}
</div>
