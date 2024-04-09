<script lang="ts">
	let defaultImages = ['windows-icon-v2.svg', 'mac-icon.svg', 'android-icon.svg', 'smiao-icon.svg'];
	let titles = ['Windows 版', 'macOS 版', 'Android 版', 'Web 版'];
	let descriptions = [
		'支持 Windows 10 及 Windows 11',
		'支持 macOS 10.11 及以上版本',
		'支持 Android 8.0 及以上系统',
		'直接打开网页使用'
	];
	let links = [
		'download/smiao-v1.0.0.msi',
		'download/smiao-v1.0.1.dmg',
		'download/smiao-v1.0.1.apk',
		'https://web.smiao.art'
	];
	let images = defaultImages.slice();
	function mouseEnter(i: number) {
		images[i] = 'download-icon-v2.svg';
		if (i === 3) {
			images[i] = 'logo.png';
		}
	}
	function mouseLeave(i: number) {
		images[i] = defaultImages[i];
	}
</script>

<div class="page-container">
	<div class="header-container">
		<a href="/" on:click|preventDefault={() => location.reload()}>
			<img src="logo.png" alt="logo" />
		</a>
		<div>喵喵静听</div>
	</div>

	<div class="content-container">
		<div class="title-container">
			<h1>喵喵静听下载</h1>
			<p>同时支持 Android，Windows， macOS 和 Web 版本</p>
		</div>

		<div class="download-container">
			{#each images as image, i}
				<div class="apps-item">
					<a
						class="apps-item-icon-box"
						tabindex={i}
						on:mouseenter={() => mouseEnter(i)}
						on:mouseleave={() => mouseLeave(i)}
						href={links[i]}
					>
						<img src={image} alt={titles[i]} />
					</a>
					<p>{titles[i]}</p>
					<p class="text-description">{descriptions[i]}</p>
				</div>
			{/each}
		</div>
	</div>
	<div class="footer">
		<p class="text-description">喵喵静听 © 2024，开发者：花心</p>
	</div>
</div>

<style>
	:global(body) :global(html) {
		height: 100%;
		background-color: #f4f4fc;
	}
	.page-container {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}
	.header-container {
		margin-top: 20px;
		margin-left: 20px;
		display: flex;
		box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
		border-radius: 10px;
	}
	.header-container > a > img {
		height: 50px;
	}
	.header-container > div {
		display: inline-block;
		margin-left: 10px;
		font-size: 1.5em;
		color: #333;
		align-self: center;
	}
	.content-container {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: flex-start;
		padding-top: 40px;
	}

	.title-container {
		font-size: 1.5em;
		text-align: center;
	}

	.download-container {
		width: 80%;
		display: flex;
		margin-top: 50px;
		align-self: center;
		justify-content: space-between;
	}
	.download-container > div {
		flex: 1;
		text-align: center;
	}
	.apps-item-icon-box {
		width: 100px;
		height: 100px;
		border: 1px solid rgba(0, 0, 0, 0.05);
		box-shadow:
			0 12px 48px rgba(77, 94, 112, 0.08),
			0 6px 16px rgba(77, 94, 112, 0.04),
			0 3px 8px rgba(77, 94, 112, 0.02);
		border-radius: 12px;
		display: flex;
		align-items: center;
		justify-content: center;
		cursor: pointer;
		position: relative;
		margin: 0 auto;
	}
	.apps-item-icon-box img {
		width: 64px;
		height: 64px;
		object-fit: contain;
	}
	.text-description {
		font-size: 0.8em;
		color: #666;
	}
	.footer {
		width: 80%;
		margin-top: auto;
		margin-bottom: auto;
		align-self: center;
		height: 50px;
	}
	@media only screen and (max-width: 600px) {
		.header-container {
			margin-top: 10px;
			margin-left: 10px;
		}
		.header-container div {
			font-size: 1em;
		}
		.content-container {
			height: 100vh;
		}
		.title-container {
			font-size: 1em;
		}
		.download-container {
			width: 100%;
			margin-top: 20px;
			flex-direction: column;
		}
	}
</style>
