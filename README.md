# Valentine
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Be My Valentine 💖</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      font-family: Arial, sans-serif;
      overflow: hidden;
    }
    .card {
      background: white;
      padding: 30px;
      border-radius: 20px;
      width: 330px;
      text-align: center;
      box-shadow: 0 15px 40px rgba(0,0,0,0.25);
      position: relative;
    }
    h1 {
      color: #ff3f6c;
    }
    p {
      font-size: 18px;
    }
    button {
      padding: 10px 22px;
      font-size: 16px;
      border: none;
      border-radius: 30px;
      cursor: pointer;
      margin: 10px;
    }
    .yes {
      background: #ff3f6c;
      color: white;
    }
    .no {
      background: #ddd;
      position: absolute;
      animation: shake 0.25s infinite;
    }
    @keyframes shake {
      0% { transform: translateX(0); }
      25% { transform: translateX(-3px); }
      50% { transform: translateX(3px); }
      75% { transform: translateX(-3px); }
      100% { transform: translateX(0); }
    }
    .heart {
      position: fixed;
      font-size: 20px;
      animation: float 4s linear forwards;
    }
    @keyframes float {
      0% { opacity: 1; transform: translateY(0); }
      100% { opacity: 0; transform: translateY(-600px); }
    }
  </style>
</head>
<body>

<div class="card" id="card">
  <h1>Hey ❤️</h1>
  <p>Answer carefully 😏</p>
  <button class="yes" onclick="next()">Start ▶️</button>
</div>

<script>
  /* ✨ CHANGE NAME HERE ✨ */
  const boyfriendName = "BABE";

  const questions = [
    `Do you like chocolates, ${boyfriendName}? 🍫`,
    `Do you like surprises? 🎁`,
    `Do you smile when you see my name? 😊`,
    `Are you free this Valentine’s Day? 🌹`,
    `So ${boyfriendName}… will you be MY Valentine? 💖`
  ];

  let index = 0;

  function moveNo(btn) {
    const card = document.getElementById("card");
    const maxX = card.clientWidth - btn.offsetWidth;
    const maxY = card.clientHeight - btn.offsetHeight;

    btn.style.left = Math.random() * maxX + "px";
    btn.style.top = Math.random() * maxY + "px";
  }

  function next() {
    if (index < questions.length - 1) {
      card.innerHTML = `
        <p>${questions[index]}</p>
        <button class="yes" onclick="next()">Yes 😍</button>
        <button class="no" id="noBtn">No 🙄</button>
      `;
      const noBtn = document.getElementById("noBtn");
      moveNo(noBtn);
      noBtn.addEventListener("mouseover", () => moveNo(noBtn));
      noBtn.addEventListener("click", () => moveNo(noBtn));
      index++;
    } else {
      celebrate();
      card.innerHTML = `
        <h1>YAYYYY 🥳</h1>
        <p>${boyfriendName}, you’re officially my Valentine 💕</p>
        <p>Screenshot this & send it to me 😘</p>
      `;
    }
  }

  function celebrate() {
    for (let i = 0; i < 40; i++) {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.innerHTML = "💖";
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.bottom = "-20px";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 4000);
    }
  }
</script>

</body>
</html>
