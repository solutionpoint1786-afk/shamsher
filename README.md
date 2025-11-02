# shamsher
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MD SHAMSHER - Ultimate E Visiting Card</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
<script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
<style>
  body, html {
    margin:0;
    padding:0;
    font-family:'Poppins', sans-serif;
    height:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    background: linear-gradient(-45deg,#6a11cb,#2575fc,#ff416c,#ff4b2b);
    background-size:400% 400%;
    animation: gradientBG 15s ease infinite;
    overflow:hidden;
  }

  @keyframes gradientBG {
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
  }

  /* Particle background */
  canvas{
    position:fixed;
    top:0;
    left:0;
    z-index:0;
  }

  /* Flip Card Container */
  .flip-card {
    background: transparent;
    width: 360px;
    height: 500px;
    perspective: 1000px;
    z-index:1;
  }

  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align:center;
    transition: transform 0.8s;
    transform-style: preserve-3d;
  }

  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  .flip-card-front, .flip-card-back {
    position: absolute;
    width:100%;
    height:100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    border-radius: 25px;
    background: rgba(255,255,255,0.15);
    backdrop-filter: blur(20px);
    color: #fff;
    box-shadow:0 15px 35px rgba(0,0,0,0.4);
    padding: 30px 20px;
    display:flex;
    flex-direction:column;
    align-items:center;
  }

  .flip-card-front h2{
    margin:10px 0 5px;
    font-weight:700;
    font-size:26px;
  }

  .flip-card-front p{
    margin:5px 0;
    font-size:16px;
    color:#e0e0e0;
  }

  .profile-img{
    width:120px;
    height:120px;
    border-radius:50%;
    border:4px solid rgba(255,255,255,0.6);
    margin-bottom:15px;
    transition: transform 0.5s;
  }

  .flip-card-front:hover .profile-img{
    transform:scale(1.1) rotateZ(5deg);
  }

  .flip-card-back{
    transform:rotateY(180deg);
    justify-content:center;
  }

  .buttons, .social-icons{
    display:flex;
    flex-wrap:wrap;
    justify-content:center;
    gap:12px;
    margin:10px 0;
  }

  .buttons a{
    text-decoration:none;
    color:#fff;
    background: rgba(255,255,255,0.2);
    padding:12px 18px;
    border-radius:15px;
    font-weight:500;
    transition:all 0.4s;
    transform-style: preserve-3d;
  }

  .buttons a:hover{
    background:#fff;
    color:#2575fc;
    transform: translateY(-5px) rotateX(5deg) rotateY(5deg);
    box-shadow:0 10px 20px rgba(0,0,0,0.3);
  }

  .social-icons a{
    color:#fff;
    font-size:22px;
    transition:all 0.4s;
  }

  .social-icons a:hover{
    color:#ffd700;
    transform:scale(1.3) rotate(10deg);
  }

  .qr img{
    width:110px;
    height:110px;
    border-radius:15px;
    border:3px solid rgba(255,255,255,0.6);
    margin-top:15px;
    transition:transform 0.3s;
  }

  .qr img:hover{
    transform: scale(1.1) rotateZ(5deg);
  }

  .copy-btn{
    margin-top:10px;
    padding:10px 15px;
    background:rgba(255,255,255,0.2);
    border:none;
    border-radius:12px;
    color:#fff;
    cursor:pointer;
    font-weight:600;
    transition:0.3s;
  }

  .copy-btn:hover{
    background:#fff;
    color:#2575fc;
    transform: translateY(-3px);
    box-shadow:0 5px 15px rgba(0,0,0,0.3);
  }

  @media(max-width:400px){
    .flip-card{width:90%; height:480px;}
  }
</style>
</head>
<body>

<canvas id="particleCanvas"></canvas>

<div class="flip-card">
  <div class="flip-card-inner">
    <div class="flip-card-front">
      <img src="https://via.placeholder.com/120" alt="Profile Picture" class="profile-img">
      <h2>MD SHAMSHER</h2>
      <p>Web Developer | Designer</p>
      <p>Renovaz.in</p>
    </div>
    <div class="flip-card-back">
      <div class="buttons">
        <a href="tel:+919876543210">Call</a>
        <a href="mailto:example@gmail.com">Email</a>
        <a href="https://wa.me/919876543210" target="_blank">WhatsApp</a>
        <a href="https://www.google.com/maps?q=Mahna+Bihar" target="_blank">Location</a>
      </div>
      <div class="social-icons">
        <a href="#" target="_blank"><i class="fab fa-facebook-f"></i></a>
        <a href="#" target="_blank"><i class="fab fa-instagram"></i></a>
        <a href="#" target="_blank"><i class="fab fa-linkedin-in"></i></a>
        <a href="#" target="_blank"><i class="fab fa-twitter"></i></a>
      </div>
      <div class="qr">
        <img src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=https://renovaz.in" alt="QR Code">
      </div>
      <button class="copy-btn" onclick="copyContact()">Copy Contact</button>
    </div>
  </div>
</div>

<script>
  // Copy phone/email to clipboard
  function copyContact(){
    const contact = "MD SHAMSHER\nPhone: +919876543210\nEmail: example@gmail.com\nWebsite: https://renovaz.in";
    navigator.clipboard.writeText(contact).then(()=>{
      alert("Contact copied to clipboard!");
    });
  }

  // Particle Background
  const canvas = document.getElementById('particleCanvas');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  let particlesArray;

  class Particle{
    constructor(x,y,size,color,weight){
      this.x=x;
      this.y=y;
      this.size=size;
      this.color=color;
      this.weight=weight;
    }
    draw(){
      ctx.fillStyle=this.color;
      ctx.beginPath();
      ctx.arc(this.x,this.y,this.size,0,Math.PI*2);
      ctx.fill();
    }
    update(){
      this.y += this.weight;
      this.x += Math.sin(this.y * 0.01);
      if(this.y>canvas.height){
        this.y=0 - this.size;
        this.x = Math.random()*canvas.width;
      }
    }
  }

  function init(){
    particlesArray=[];
    for(let i=0;i<100;i++){
      let size=Math.random()*3+1;
      let x=Math.random()*canvas.width;
      let y=Math.random()*canvas.height;
      let color='rgba(255,255,255,0.7)';
      let weight=Math.random()*1+0.5;
      particlesArray.push(new Particle(x,y,size,color,weight));
    }
  }

  function animate(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    for(let i=0;i<particlesArray.length;i++){
      particlesArray[i].draw();
      particlesArray[i].update();
    }
    requestAnimationFrame(animate);
  }

  init();
  animate();

  window.addEventListener('resize',()=>{
    canvas.width=window.innerWidth;
    canvas.height=window.innerHeight;
    init();
  });
</script>

</body>
</html>
