<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Happy Birthday, Sayang! 🎂</title>
  <meta name="description" content="Ucapan ulang tahun interaktif dari Rizki 💖" />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&family=Pacifico&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#fff7fb;
      --card:#ffffff;
      --ink:#2b2b2b;
      --accent:#ff6fb1;
      --accent2:#7c4dff;
      --soft:#ffd1e8;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family:"Poppins",system-ui,-apple-system,Segoe UI,Roboto,Helvetica,Arial,"Apple Color Emoji","Segoe UI Emoji";
      color:var(--ink);
      background: radial-gradient(1200px 600px at 80% -10%, #ffe9f6, transparent 60%),
                  radial-gradient(900px 500px at -10% 10%, #efe7ff, transparent 60%),
                  var(--bg);
      overflow-x:hidden;
    }
    .container{max-width:960px;margin:0 auto;padding:24px}
    header{
      display:flex;flex-direction:column;align-items:center;gap:12px;padding:48px 12px 24px
    }
    h1{
      font-family:"Pacifico", cursive; font-size: clamp(36px,6vw,64px);
      margin:0;line-height:1.1; color:#ff3e9e; text-shadow:0 6px 20px rgba(255,62,158,.25)
    }
    h2{margin:0;font-weight:700;letter-spacing:.5px}
    p.lead{margin:0;opacity:.85}
    .card{background:var(--card); border-radius:24px; box-shadow:0 10px 30px rgba(0,0,0,.08); padding:24px}

    .cta{
      display:inline-flex;align-items:center;gap:10px;cursor:pointer;border:none;
      padding:14px 20px;border-radius:999px;font-weight:700;font-size:16px;
      background:linear-gradient(135deg,var(--accent),var(--accent2)); color:#fff;
      box-shadow:0 10px 30px rgba(124,77,255,.35); transition:transform .15s ease, filter .15s ease
    }
    .cta:active{transform:translateY(1px)}

    .hidden{display:none}
    .center{text-align:center}

    /* Balloons */
    .balloons{position:relative;height:180px;pointer-events:none}
    .balloon{position:absolute;bottom:-30px;width:70px;height:90px;border-radius:50% 50% 45% 55% / 55% 50% 50% 45%;
      filter:drop-shadow(0 8px 14px rgba(0,0,0,.12)); animation:float 6s ease-in-out infinite
    }
    .balloon:after{content:""; position:absolute;left:50%;top:88px; width:2px;height:50px;background:rgba(0,0,0,.12)}
    @keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-18px)}}

    /* Typewriter */
    .type{font-size:18px;line-height:1.7; white-space:pre-wrap; min-height:140px}
    .cursor{display:inline-block;width:8px;background:#333;margin-left:2px;animation:blink 1s step-end infinite}
    @keyframes blink{50%{opacity:0}}

    /* Gallery */
    .grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(180px,1fr)); gap:12px}
    .photo{position:relative;border-radius:16px; overflow:hidden; aspect-ratio:1/1; background:#f6f6f8}
    .photo img{width:100%;height:100%;object-fit:cover; display:block}

    /* Quiz */
    .quiz q{font-weight:600}
    .opt{display:block;margin:.5rem 0;padding:.8rem 1rem;border:2px solid #eee;border-radius:12px;cursor:pointer}
    .opt:hover{border-color:#ffd1e8}
    .opt.correct{border-color:#48c774;background:#e7fff1}
    .opt.wrong{border-color:#ff7a7a;background:#fff1f1}

    /* Floating hearts */
    .hearts{position:fixed; inset:0; pointer-events:none; overflow:hidden}
    .heart{position:absolute; font-size:22px; animation:rise 6s linear forwards; opacity:.8}
    @keyframes rise{to{transform:translateY(-120vh) scale(1.8); opacity:0}}

    footer{padding:40px 12px;text-align:center;opacity:.7}
    .note{font-size:12px}

    /* Canvas confetti */
    #confetti{position:fixed; inset:0; pointer-events:none}
  </style>
</head>
<body>
  <canvas id="confetti"></canvas>
  <div class="hearts" id="hearts"></div>
  <div class="container">
    <header class="center">
      <div class="balloons" aria-hidden="true"></div>
      <h1>Happy Birthday, Sayang! 🎂💖</h1>
      <p class="lead">Walau kita lagi LDR, semoga halaman kecil ini bikin kamu merasa dipeluk dari jauh. — Rizki</p>
      <br />
      <button class="cta" id="openBtn">🎉 Buka Surprisenya</button>
    </header>

    <section id="message" class="card hidden">
      <h2>Pesan untukmu</h2>
      <div class="type" id="type"></div>
    </section>

    <section id="gallery" class="card hidden" style="margin-top:16px">
      <h2>Galeri Kenangan Kita 📸</h2>
      <p class="note">Ganti link gambar di file ini nanti (cari <code>src</code>) untuk pakai foto kalian sendiri.</p>
      <div class="grid">
        <div class="photo"><img src="https://images.unsplash.com/photo-1526925539332-aa3b66e35444?q=80&w=800&auto=format&fit=crop" alt="momen 1"></div>
        <div class="photo"><img src="https://images.unsplash.com/photo-1518709268805-4e9042af9f23?q=80&w=800&auto=format&fit=crop" alt="momen 2"></div>
        <div class="photo"><img src="https://images.unsplash.com/photo-1518199266791-5375a83190b7?q=80&w=800&auto=format&fit=crop" alt="momen 3"></div>
        <div class="photo"><img src="https://images.unsplash.com/photo-1488166986004-876cfc650e9a?q=80&w=800&auto=format&fit=crop" alt="momen 4"></div>
      </div>
    </section>

    <section id="quiz" class="card hidden" style="margin-top:16px">
      <h2>Mini Quiz Cinta 💕</h2>
      <div class="quiz">
        <p><q>Kapan kita pertama kali video call lama-lama?</q></p>
        <label class="opt"><input type="radio" name="q1" value="wrong"> 1 Januari</label>
        <label class="opt"><input type="radio" name="q1" value="correct"> 14 Februari</label>
        <label class="opt"><input type="radio" name="q1" value="wrong"> 17 Agustus</label>
        <p><q>Makanan favorit kamu yang sering kita bahas?</q></p>
        <label class="opt"><input type="radio" name="q2" value="correct"> Mie ayam</label>
        <label class="opt"><input type="radio" name="q2" value="wrong"> Sushi</label>
        <label class="opt"><input type="radio" name="q2" value="wrong"> Pizza</label>
        <p><q>Destinasi impian kita?</q></p>
        <label class="opt"><input type="radio" name="q3" value="wrong"> Bali</label>
        <label class="opt"><input type="radio" name="q3" value="correct"> Jepang</label>
        <label class="opt"><input type="radio" name="q3" value="wrong"> Korea</label>
        <br>
        <button class="cta" id="submitQuiz">✨ Selesai</button>
        <p id="quizMsg" style="margin-top:10px"></p>
      </div>
    </section>

    <section id="final" class="card hidden" style="margin-top:16px">
      <h2>Untuk Penutup… ✨</h2>
      <p>Semoga tahun ini penuh hal-hal manis, rezeki yang lancar, dan langkah yang makin dekat sama mimpi-mimpi kamu. Terima kasih sudah jadi rumah paling hangat buat hatiku. I love you. 💌</p>
    </section>

    <footer>
      <small class="note">Made with 💗 by Rizki — kirim link halaman ini ke dia tepat di jam 00.00 😉</small>
    </footer>
  </div>

  <script>
    // Balloons generator
    const balloonColors = ["#FF8BC6","#84A7FF","#FFD166","#B5F7D2","#FFAF87"]; 
    const balloons = document.querySelector('.balloons');
    for(let i=0;i<8;i++){
      const b=document.createElement('div');
      b.className='balloon';
      b.style.left = (i*12 + Math.random()*8) + '%';
      const c = balloonColors[i%balloonColors.length];
      b.style.background = `radial-gradient(circle at 30% 25%, #fff7, transparent 40%), ${c}`;
      b.style.animationDelay = (Math.random()*2)+'s';
      balloons.appendChild(b);
    }

    // Typewriter text
    const text = `Selamat ulang tahun, sayangku!\n\nTerima kasih sudah bertahan dan percaya sama kita meski jarak sering nakal. Aku bangga sama kamu—dengan semua usaha, tawa, dan sabar yang kamu punya. Doaku: sehat, bahagia, rezeki lancar, dan setiap harimu dipenuhi rasa dicintai.\n\nTunggu aku ya. Aku selalu menuju kamu. ❤️`;
    const typeBox = document.getElementById('type');

    function typeWriter(el, str, speed=24){
      let i=0; el.innerHTML='';
      const cursor=document.createElement('span'); cursor.className='cursor'; el.appendChild(cursor);
      const timer=setInterval(()=>{
        if(i>=str.length){ clearInterval(timer); cursor.remove(); return; }
        const ch = str[i++] ;
        cursor.insertAdjacentText('beforebegin', ch);
      }, speed);
    }

    // Hearts animation
    const hearts = document.getElementById('hearts');
    function popHearts(n=12){
      for(let i=0;i<n;i++){
        const h=document.createElement('div');
        h.className='heart';
        h.textContent = Math.random()>.5 ? '💗' : '💖';
        h.style.left = (Math.random()*100)+'vw';
        h.style.bottom = '-10vh';
        h.style.transform = `translateY(0) scale(${1+Math.random()*1.2})`;
        h.style.animationDuration = (5+Math.random()*3)+'s';
        hearts.appendChild(h);
        setTimeout(()=>h.remove(),8000);
      }
    }

    // Canvas confetti (tiny)
    const confettiCanvas = document.getElementById('confetti');
    const ctx = confettiCanvas.getContext('2d');
    function resize(){ confettiCanvas.width = innerWidth; confettiCanvas.height = innerHeight; }
    addEventListener('resize', resize); resize();
    let confettiPieces=[];
    function shootConfetti(){
      const colors=['#ff6fb1','#7c4dff','#ffd166','#4ade80','#60a5fa'];
      for(let i=0;i<180;i++){
        confettiPieces.push({
          x: innerWidth/2 + (Math.random()*120-60),
          y: innerHeight/2,
          a: Math.random()*Math.PI*2,
          v: 2+Math.random()*5,
          s: 4+Math.random()*6,
          r: Math.random()*Math.PI,
          c: colors[Math.floor(Math.random()*colors.length)],
          g: .02+Math.random()*.04
        })
      }
    }
    function drawConfetti(){
      ctx.clearRect(0,0,confettiCanvas.width, confettiCanvas.height);
      confettiPieces.forEach(p=>{
        p.x += Math.cos(p.a)*p.v; p.y += Math.sin(p.a)*p.v + p.g*50; p.r += .05; p.v *= .99;
        ctx.save(); ctx.translate(p.x,p.y); ctx.rotate(p.r);
        ctx.fillStyle = p.c; ctx.fillRect(-p.s/2,-p.s/2,p.s,p.s);
        ctx.restore();
      });
      confettiPieces = confettiPieces.filter(p=> p.y < innerHeight+40);
      requestAnimationFrame(drawConfetti);
    }
    drawConfetti();

    // Open flow
    const openBtn = document.getElementById('openBtn');
    const sections = ['message','gallery','quiz','final'].map(id=>document.getElementById(id));
    openBtn.addEventListener('click',()=>{
      shootConfetti(); popHearts(20);
      sections.forEach((s,i)=> setTimeout(()=> s.classList.remove('hidden'), i*600));
      typeWriter(typeBox, text, 16);
      openBtn.disabled = true; openBtn.textContent = '❤️ Selamat Menikmati!';
    });

    // Quiz logic
    function mark(group){
      document.querySelectorAll('input[name="'+group+'"]').forEach(i=>{
        const label = i.closest('.opt');
        label.classList.remove('correct','wrong');
        if(i.checked){ label.classList.add(i.value==='correct'?'correct':'wrong'); }
      });
    }
    ['q1','q2','q3'].forEach(name=>{
      document.querySelectorAll('input[name="'+name+'"]').forEach(r=>{
        r.addEventListener('change',()=>mark(name));
      })
    })
    document.getElementById('submitQuiz').addEventListener('click',()=>{
      const ok1 = document.querySelector('input[name="q1"]:checked')?.value==='correct';
      const ok2 = document.querySelector('input[name="q2"]:checked')?.value==='correct';
      const ok3 = document.querySelector('input[name="q3"]:checked')?.value==='correct';
      const msg = document.getElementById('quizMsg');
      if(ok1 && ok2 && ok3){ msg.textContent = 'Yeay! Semua benar. Kamu paling kenal aku. 💞'; popHearts(25); shootConfetti(); }
      else { msg.textContent='Hampir! Coba cek lagi jawabannya yaa 😘'; }
    });
  </script>
</body>
</html>
