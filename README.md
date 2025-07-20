<!DOCTYPE html><html lang="bn">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Nexg News</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f4f4f4;
    }
    header {
      background-color: #1a237e;
      color: white;
      padding: 20px;
      text-align: center;
    }
    nav {
      display: flex;
      justify-content: center;
      background-color: #3949ab;
      flex-wrap: wrap;
    }
    nav a {
      color: white;
      padding: 14px 20px;
      text-decoration: none;
      display: block;
    }
    nav a:hover {
      background-color: #303f9f;
    }
    .search-contact {
      display: flex;
      justify-content: space-between;
      padding: 10px 20px;
      background-color: #e8eaf6;
    }
    .search-contact input[type="text"] {
      padding: 8px;
      width: 60%;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    .search-contact button {
      padding: 8px 12px;
      background-color: #1a237e;
      color: white;
      border: none;
      border-radius: 4px;
    }
    .container {
      padding: 20px;
    }
    .news-item {
      background-color: white;
      padding: 15px;
      margin-bottom: 15px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .news-item h2 {
      margin: 0 0 10px;
    }
    .news-item p {
      margin: 0;
    }
    footer {
      background-color: #1a237e;
      color: white;
      text-align: center;
      padding: 10px;
      position: fixed;
      width: 100%;
      bottom: 0;
    }
    #admin-panel {
      padding: 20px;
      background-color: #fff;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      margin: 20px;
    }
    #admin-panel input, #admin-panel textarea {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
  </style>
</head>
<body>  <header>
    <h1>Nexg News</h1>
    <p>সত্য খবর, আপনার জন্য</p>
  </header>  <nav>
    <a href="#">জাতীয়</a>
    <a href="#">আন্তর্জাতিক</a>
    <a href="#">খেলাধুলা</a>
    <a href="#">বিনোদন</a>
    <a href="#">প্রযুক্তি</a>
  </nav>  <div class="search-contact">
    <input type="text" id="search" placeholder="খবর খুঁজুন...">
    <button onclick="searchNews()">সার্চ</button>
    <button onclick="alert('যোগাযোগ: contact@nexgnews.com')">যোগাযোগ</button>
  </div>  <div class="container" id="news-container">
    <!-- Dynamic news will be loaded here -->
  </div>  <div id="admin-panel">
    <h3>অ্যাডমিন প্যানেল</h3>
    <input type="text" id="admin-title" placeholder="খবরের শিরোনাম">
    <textarea id="admin-body" rows="4" placeholder="খবরের বিস্তারিত"></textarea>
    <button onclick="addNews()">নতুন খবর যোগ করুন</button>
  </div>  <footer>
    &copy; 2025 Nexg News. সর্বস্বত্ব সংরক্ষিত।
  </footer>  <script>
    // Simulate fetching news from API
    const newsAPI = [
      { title: "আজ দেশের তাপমাত্রা ৩৫ ডিগ্রি", body: "সারা দেশে তীব্র গরম পড়েছে। জনজীবন অতিষ্ঠ।" },
      { title: "বিশ্বকাপ ফুটবলে বাংলাদেশের স্বপ্ন ভাঙলো", body: "শেষ মুহূর্তের গোলে হেরে গেছে বাংলাদেশ।" }
    ];

    function loadNews() {
      const container = document.getElementById('news-container');
      container.innerHTML = '';
      newsAPI.forEach(news => {
        const item = document.createElement('div');
        item.className = 'news-item';
        item.innerHTML = `<h2>${news.title}</h2><p>${news.body}</p>`;
        container.appendChild(item);
      });
    }

    function addNews() {
      const title = document.getElementById('admin-title').value;
      const body = document.getElementById('admin-body').value;
      if (title && body) {
        newsAPI.unshift({ title, body });
        loadNews();
        document.getElementById('admin-title').value = '';
        document.getElementById('admin-body').value = '';
      } else {
        alert('দয়া করে শিরোনাম ও বিস্তারিত দিন');
      }
    }

    function searchNews() {
      const query = document.getElementById('search').value.toLowerCase();
      const filtered = newsAPI.filter(n => n.title.toLowerCase().includes(query) || n.body.toLowerCase().includes(query));
      const container = document.getElementById('news-container');
      container.innerHTML = '';
      if (filtered.length) {
        filtered.forEach(news => {
          const item = document.createElement('div');
          item.className = 'news-item';
          item.innerHTML = `<h2>${news.title}</h2><p>${news.body}</p>`;
          container.appendChild(item);
        });
      } else {
        container.innerHTML = '<p>কোনো ফলাফল পাওয়া যায়নি।</p>';
      }
    }

    window.onload = loadNews;
  </script></body>
</html>
