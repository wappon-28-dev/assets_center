<script lang="ts">
  import { page } from "$app/stores";
  import type { PageManifest } from "$lib/model/manifests";
  import { MetaTags } from "svelte-meta-tags";

  export let pageManifest: PageManifest;

  const meta = pageManifest.meta;
  const title =
    meta.title !== undefined
      ? `${meta.title} | Assets Center`
      : "Assets Center";
  const description =
    meta.description ?? "Assets Center powered by wappon_28_dev.";
  const imgUrl = meta.ogp.img ?? "https://iili.io/HXx1Vsf.png";

  const url = $page.url.toString();
</script>

<MetaTags
  {title}
  {description}
  canonical={url}
  openGraph={{
    type: "website",
    url,
    title,
    description,
    images: [
      {
        url: imgUrl,
        width: 1200,
        height: 630,
        alt: title,
      },
    ],
  }}
/>
