<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Ella</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&family=Nunito:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --peach:#FFE3CC;
    --blush:#FFB6A9;
    --rose:#E8637A;
    --cream:#FFF7EF;
    --plum:#3E2A34;
    --mint:#AEE3C6;
    --sun:#FFD469;
    --radius-lg: 28px;
    --radius-sm: 14px;
  }

  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--cream);
    color:var(--plum);
    font-family:'Nunito', sans-serif;
    overflow-x:hidden;
  }
  h1,h2,h3,.display{
    font-family:'Fredoka', sans-serif;
    font-weight:600;
    margin:0;
  }
  p{line-height:1.6; margin:0 0 1em 0;}
  .wrap{max-width:640px; margin:0 auto; padding:0 24px;}

  #opener{
    position:fixed; inset:0; z-index:50;
    background:linear-gradient(160deg,var(--blush),var(--peach));
    display:flex; align-items:center; justify-content:center;
    flex-direction:column;
    transition:transform 0.9s cubic-bezier(.65,0,.35,1), opacity 0.9s ease;
  }
  #opener.opened{
    transform:translateY(-100%);
    opacity:0.4;
    pointer-events:none;
  }
  .envelope{
    width:220px; height:150px;
    position:relative;
    cursor:pointer;
    filter:drop-shadow(0 18px 30px rgba(62,42,52,0.25));
  }
  .env-body{
    position:absolute; inset:0;
    background:var(--cream);
    border-radius:10px;
  }
  .env-flap{
    position:absolute; top:0; left:0; width:100%; height:75px;
    background:var(--rose);
    clip-path:polygon(0 0, 100% 0, 50% 90%);
    transform-origin:top center;
    transition:transform 0.6s ease;
    border-radius:10px 10px 0 0;
  }
  .envelope.open .env-flap{ transform:rotateX(180deg); }
  .env-heart{
    position:absolute; top:52%; left:50%; transform:translate(-50%,-50%);
    font-size:28px;
  }
  .opener-hint{
    margin-top:28px;
    font-family:'Fredoka', sans-serif;
    font-size:15px;
    color:var(--plum);
    opacity:0.75;
  }

  .hero{
    min-height:100vh;
    display:flex; flex-direction:column; justify-content:center; align-items:center;
    text-align:center;
    padding:80px 24px 60px;
    position:relative;
    background:radial-gradient(circle at 20% 15%, var(--peach) 0%, var(--cream) 55%);
  }
  .hero .display{
    font-size:clamp(2.2rem, 7vw, 3.6rem);
    line-height:1.15;
    color:var(--rose);
  }
  .hero .sub{
    margin-top:18px;
    font-size:1.1rem;
    max-width:420px;
    color:var(--plum);
    opacity:0.85;
  }
  .doodle-row{
    margin-top:36px;
    font-size:1.6rem;
    letter-spacing:14px;
  }

  section{ padding:70px 0; }
  .section-title{
    font-size:1.7rem;
    color:var(--rose);
    text-align:center;
    margin-bottom:10px;
  }
  .section-lede{
    text-align:center;
    max-width:420px;
    margin:0 auto 40px;
    opacity:0.75;
  }
  .stat-row{
    display:flex;
    gap:16px;
    flex-wrap:wrap;
    justify-content:center;
  }
  .stat-blob{
    background:var(--blush);
    border-radius:50% 50% 46% 54% / 54% 46% 54% 46%;
    width:150px; height:150px;
    display:flex; flex-direction:column; align-items:center; justify-content:center;
    text-align:center;
    padding:10px;
  }
  .stat-blob:nth-child(2){ background:var(--mint); }
  .stat-blob:nth-child(3){ background:var(--sun); }
  .stat-num{
    font-family:'Fredoka', sans-serif;
    font-size:1.9rem;
    color:var(--plum);
  }
  .stat-label{
    font-size:0.78rem;
    margin-top:4px;
    max-width:100px;
  }

  .reasons-list{
    display:flex;
    flex-direction:column;
    gap:14px;
  }
  .reason-card{
    background:var(--cream);
    border:2px solid var(--peach);
    border-radius:var(--radius-sm);
    padding:18px 20px;
    display:flex;
    gap:14px;
    align-items:flex-start;
    transition:transform 0.25s ease, border-color 0.25s ease;
  }
  .reason-card:hover{
    transform:translateX(4px);
    border-color:var(--rose);
  }
  .reason-mark{
    font-size:1.3rem;
    line-height:1;
    flex-shrink:0;
  }
  .reason-text{font-size:0.98rem;}

  .gallery{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:18px;
  }
  .frame{
    background:linear-gradient(150deg,var(--peach),var(--blush));
    border-radius:var(--radius-sm);
    aspect-ratio:1/1;
    display:flex; align-items:center; justify-content:center;
    text-align:center;
    padding:16px;
    font-size:0.85rem;
    color:var(--plum);
    transform:rotate(var(--r,0deg));
    overflow:hidden;
  }
  .frame img{ width:100%; height:100%; object-fit:cover; border-radius:inherit; }
  .frame:nth-child(4n+1){ --r:-3deg; }
  .frame:nth-child(4n+2){ --r:2deg; }
  .frame:nth-child(4n+3){ --r:-2deg; }
  .frame:nth-child(4n+4){ --r:3deg; }
  @media (min-width:560px){
    .gallery{ grid-template-columns:repeat(3,1fr); }
  }

  .letter-card{
    background:var(--cream);
    border-radius:var(--radius-lg);
    border:2px solid var(--peach);
    padding:40px 32px;
    position:relative;
  }
  .letter-card p{ font-size:1.02rem; }
  .signature{
    margin-top:24px;
    font-family:'Fredoka', sans-serif;
    font-size:1.3rem;
    color:var(--rose);
  }

  footer{
    text-align:center;
    padding:50px 24px 70px;
    font-size:0.85rem;
    opacity:0.55;
  }

  @media (prefers-reduced-motion: reduce){
    html{scroll-behavior:auto;}
    #opener, .env-flap, .reason-card{transition:none;}
  }

  button:focus-visible, .envelope:focus-visible{
    outline:3px solid var(--rose);
    outline-offset:4px;
  }
</style>
</head>
<body>

<div id="opener">
  <div class="envelope" id="envelope" role="button" tabindex="0" aria-label="Open the letter">
    <div class="env-flap"></div>
    <div class="env-body"></div>
    <div class="env-heart">💌</div>
  </div>
  <div class="opener-hint">tap the envelope</div>
</div>

<section class="hero">
  <div class="wrap">
    <h1 class="display">Hi, my love.<br>I made you a little website.</h1>
    <p class="sub">Not for anyone else — just for you. Scroll down, there's more.</p>
    <div class="doodle-row">🌷 💛 🫶</div>
  </div>
</section>

<section>
  <div class="wrap">
    <h2 class="section-title">Us, in numbers</h2>
    <p class="section-lede">Since September 29, 2024.</p>
    <div class="stat-row">
      <div class="stat-blob">
        <div class="stat-num" id="dayCount">-</div>
        <div class="stat-label">days together</div>
      </div>
    </div>
  </div>
</section>
<section>
  <div class="wrap">
    <div class="letter-card">
      <p>Ella, I wanted to make something small and a little silly, just to say thank you for being you. For every ordinary day you've made feel like it mattered, and every hard one you made easier just by being there.</p>
      <p>This site isn't much — a few blobs, an envelope, and some words that don't quite capture it — but I wanted you to have something that's just ours.</p>
      <p>Here's to three years, and all the ones still coming.</p>
      <div class="signature">— Sam</div>
    </div>
  </div>
</section>

<footer>made with love, one line of code at a time</footer>

<script>
  const opener = document.getElementById('opener');
  const envelope = document.getElementById('envelope');
  function openLetter(){
    envelope.classList.add('open');
    setTimeout(()=> opener.classList.add('opened'), 500);
  }
  envelope.addEventListener('click', openLetter);
  envelope.addEventListener('keypress', (e)=>{
    if(e.key === 'Enter' || e.key === ' ') openLetter();
  });

  const startDate = new Date('2024-09-29');
  const today = new Date();
  const diffDays = Math.floor((today - startDate) / (1000 * 60 * 60 * 24));
  document.getElementById('dayCount').textContent = diffDays > 0 ? diffDays.toLocaleString() : '—';
</script>

</body>
</html>
