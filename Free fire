<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mini Free Fire 2D</title>
<style>
  body {
    margin: 0;
    overflow: hidden;
    background: #222;
  }
  canvas {
    display: block;
    background: #333;
  }
</style>
</head>
<body>

<canvas id="game"></canvas>

<script>
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

// Player
let player = {
  x: canvas.width / 2,
  y: canvas.height / 2,
  size: 20,
  color: "lime",
  speed: 4
};

// Bullets
let bullets = [];

// Controls (mobile + teclado)
let keys = {};

window.addEventListener("keydown", e => keys[e.key] = true);
window.addEventListener("keyup", e => keys[e.key] = false);

// Toque na tela atira
canvas.addEventListener("touchstart", shoot);
canvas.addEventListener("click", shoot);

function shoot() {
  bullets.push({
    x: player.x,
    y: player.y,
    dx: 0,
    dy: -6,
    size: 5
  });
}

// Movimento
function movePlayer() {
  if (keys["w"] || keys["ArrowUp"]) player.y -= player.speed;
  if (keys["s"] || keys["ArrowDown"]) player.y += player.speed;
  if (keys["a"] || keys["ArrowLeft"]) player.x -= player.speed;
  if (keys["d"] || keys["ArrowRight"]) player.x += player.speed;
}

// Atualizar balas
function updateBullets() {
  bullets.forEach((b, i) => {
    b.y += b.dy;
    if (b.y < 0) bullets.splice(i, 1);
  });
}

// Desenhar
function drawPlayer() {
  ctx.fillStyle = player.color;
  ctx.fillRect(player.x, player.y, player.size, player.size);
}

function drawBullets() {
  ctx.fillStyle = "yellow";
  bullets.forEach(b => {
    ctx.fillRect(b.x, b.y, b.size, b.size);
  });
}

// Loop do jogo
function gameLoop() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  movePlayer();
  updateBullets();

  drawPlayer();
  drawBullets();

  requestAnimationFrame(gameLoop);
}

gameLoop();
</script>

</body>
</html>
