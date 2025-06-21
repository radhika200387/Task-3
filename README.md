<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Advanced Web Demo</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      margin: 0;
      background: #f4f4f4;
      color: #333;
    }

    h1 {
      color: #4CAF50;
      text-align: center;
    }

    /* === Carousel Styling === */
    .carousel-container {
      text-align: center;
      margin: 30px 0;
    }

    img#carousel {
      width: 300px;
      height: 200px;
      border-radius: 10px;
    }

    button {
      margin: 10px;
      padding: 10px 20px;
      border: none;
      background-color: #4CAF50;
      color: white;
      font-size: 16px;
      cursor: pointer;
      border-radius: 5px;
    }

    /* === Joke Section === */
    .joke-container {
      margin-top: 40px;
      text-align: center;
    }

    #joke {
      font-size: 18px;
      margin-top: 10px;
      background: #fff;
      padding: 15px;
      border-radius: 8px;
      box-shadow: 0 0 8px rgba(0,0,0,0.1);
      max-width: 500px;
      margin-left: auto;
      margin-right: auto;
    }

    /* === Responsive Design === */
    @media (max-width: 768px) {
      img#carousel {
        width: 90%;
        height: auto;
      }

      body {
        padding: 10px;
        font-size: 15px;
      }
    }
  </style>
</head>
<body>

  <h1>🌐 Advanced Web Project</h1>

  <!-- === Step 2: Image Carousel === -->
  <div class="carousel-container">
    <h2>🖼️ Image Carousel</h2>
    <img id="carousel" src="https://picsum.photos/id/1015/300/200" alt="carousel image" />
    <br>
    <button onclick="prevImage()">Previous</button>
    <button onclick="nextImage()">Next</button>
  </div>

  <!-- === Step 3: Joke API === -->
  <div class="joke-container">
    <h2>😂 Get a Random Joke</h2>
    <button onclick="getJoke()">Get Joke</button>
    <div id="joke">Click the button to load a joke!</div>
  </div>

  <script>
    // === Image Carousel Logic ===
    const images = [
      "https://picsum.photos/id/1015/300/200",
      "https://picsum.photos/id/1016/300/200",
      "https://picsum.photos/id/1018/300/200",
      "https://picsum.photos/id/1020/300/200"
    ];
    let index = 0;

    function showImage() {
      document.getElementById("carousel").src = images[index];
    }

    function nextImage() {
      index = (index + 1) % images.length;
      showImage();
    }

    function prevImage() {
      index = (index - 1 + images.length) % images.length;
      showImage();
    }

    // === Fetch Joke from Public API ===
    async function getJoke() {
      try {
        const res = await fetch("https://official-joke-api.appspot.com/random_joke");
        const data = await res.json();
        document.getElementById("joke").innerText = `${data.setup} — ${data.punchline}`;
      } catch (error) {
        document.getElementById("joke").innerText = "Failed to load joke.";
      }
    }
  </script>

</body>
</html>
