<svelte:head>
  <title>文字数カウント</title>
  <meta name="description" content="テキストボックスに入力された文字数をカウントします">
  <meta property="og:title" content="文字数カウント">
  <meta property="og:description" content="テキストボックスに入力された文字数をカウントします">
  <meta property="og:url" content="https://tools.kattyan.dev/">
  <meta property="og:image" content="https://www.example.com/mypage/og-image.jpg">
</svelte:head>


<script>
    let text = "";
    let totalChars = 0;
    let noSpaceChars = 0;
    let noUrlChars = 0;
  
    function updateCount() {
      totalChars = text.length;
      noSpaceChars = text.replace(/\s/g, '').length;
  
      // Removing URLs from the text
      let textNoUrl = text.replace(/(https?:\/\/[^\s]+)/g, '');
      noUrlChars = textNoUrl.replace(/\s/g, '').length;
    }
  </script>
  
  <main class="flex flex-col items-center justify-center min-h-screen bg-gray-100 py-2">
    <h1 class="text-4xl font-bold mb-5 text-blue-700">文字数カウント</h1>
    
    <textarea 
      bind:value={text} 
      on:input={updateCount} 
      placeholder="テキストを入力してください"
      class="w-3/4 h-64 px-3 py-2 text-lg placeholder-gray-500 text-gray-900 rounded-md focus:outline-none focus:shadow-outline-blue focus:border-blue-300 mb-5"
    ></textarea>
    
    <div class="text-lg">
      <p class="mb-2">文字数: {totalChars}</p>
      <p class="mb-2">空白除外文字数: {noSpaceChars}</p>
      <p class="mb-2">URLと空白除外文字数: {noUrlChars}</p>
    </div>
  </main>
  