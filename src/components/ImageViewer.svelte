<script>
    import { resource } from '../SmartOnFhirStore.js';

    let data = null;
    let contentType = null;
    let url = null;
    
    $: {
        data = $resource?.content[0].attachment?.data;
        contentType = $resource?.content[0].contentType;
        url = $resource?.content[0].attachment.url;
    }
</script>


<div class="image-viewer">
    {#if url}
        <img alt="jpeg" src="{url}"/>
    {:else if data}
        <img alt="jpeg" src="data:{contentType};base64,{data}"/>
    {/if}
</div>


<style>
    .image-viewer {
        overflow: auto;
        height: 100%;
        width:100%;
        background-color: rgb(77, 77, 77);        
    }
</style>