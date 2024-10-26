# Jogo Pong em JavaScript

Este projeto implementa uma versão simplificada do jogo Pong utilizando JavaScript e a biblioteca p5.js. Ele inclui controle das raquetes pelo jogador e pelo computador, colisões com sons e um sistema de pontuação com narração.

## Funcionalidades

- **Controle da Raquete do Jogador:** Movimenta a raquete com o mouse.
- **IA para Raquete do Computador:** A raquete do computador segue a posição da bola automaticamente.
- **Colisões da Bola:** A bola rebate ao colidir com as bordas, raquetes e barras superior e inferior.
- **Pontuação e Narração:** Pontuação é atualizada ao ultrapassar as raquetes, com narração do placar.
- **Efeitos Sonoros:** Sons específicos para colisões e gols.

## Estrutura do Código

### Inicialização de Variáveis e Recursos

As variáveis e recursos são carregados na função `preload()`, onde imagens e sons são preparados para o jogo.

```javascript
let raqueteJogador, raqueteComputador, bola, barraSuperior, barraInferior;
let fundoImg, bolaImg, barra1Img, barra2Img;
let bounceSound, golSound;

let placarJogador = 0;
let placarComputador = 0;

function preload() {
  fundoImg = loadImage('fundo1.png');
  bolaImg = loadImage('bola.png');
  barra1Img = loadImage('barra01.png');
  barra2Img = loadImage('barra02.png');
  bounceSound = loadSound('446100__justinvoke__bounce.wav');
  golSound = loadSound('274178__littlerobotsoundfactory__jingle_win_synth_02.wav');
}
Configuração Inicial
Na função setup(), o canvas é criado e os objetos para as raquetes, a bola e as barras são instanciados.

javascript
Copiar código
function setup() {
  createCanvas(800, 400);
  raqueteJogador = new Raquete(30, height / 2, 10, 60);
  raqueteComputador = new Raquete(width - 40, height / 2, 10, 60);
  bola = new Bola(10);
  barraSuperior = new Barra(0, 0, width, 5);
  barraInferior = new Barra(0, height, width, 5);
}
Loop Principal de Jogo
A função draw() atualiza e desenha os elementos na tela continuamente:

Desenha o fundo.
Atualiza a posição da bola e das raquetes.
Detecta colisões entre a bola e as raquetes.
Exibe as raquetes, bola e barras.
javascript
Copiar código
function draw() {
  image(fundoImg, imgX, imgY, imgWidth, imgHeight);
  raqueteJogador.atualizar();
  raqueteComputador.atualizar();
  bola.atualizar(barraSuperior, barraInferior);
  bola.verificarColisaoRaquete(raqueteJogador);
  bola.verificarColisaoRaquete(raqueteComputador);
  raqueteJogador.exibir();
  raqueteComputador.exibir();
  bola.exibir();
  barraSuperior.exibir();
  barraInferior.exibir();
}
Classes
Classe Raquete
Define o comportamento de cada raquete, controlando seu movimento e exibição. A raquete do jogador segue o mouse, enquanto a do computador segue a bola.

javascript
Copiar código
class Raquete {
  constructor(x, y, w, h) { ... }

  atualizar() { ... } // Movimenta a raquete
  exibir() { ... }    // Desenha a raquete
}
Classe Bola
Controla a posição, movimento e colisões da bola, além de aumentar a velocidade a cada colisão.

javascript
Copiar código
class Bola {
  constructor(r) { ... }
  
  atualizar(barraSuperior, barraInferior) { ... } // Atualiza a posição da bola
  verificarColisaoRaquete(raquete) { ... }       // Detecta colisão com raquetes
  exibir() { ... }                               // Desenha a bola
}
Classe Barra
Representa as bordas superior e inferior do campo, impedindo que a bola saia pela parte superior ou inferior.

javascript
Copiar código
class Barra {
  constructor(x, y, w, h) { ... }
  exibir() { ... }  // Desenha a barra
}
Funções Auxiliares
tocarSomColisao(): Toca o som de colisão da bola com as raquetes.
tocarSomDeGol(): Toca o som quando a bola passa pelas raquetes e marca um gol.
narrarPlacar(): Narra o placar atual utilizando síntese de voz.
Dependências
p5.js: Biblioteca para manipulação de gráficos e áudio.
Recursos do jogo:
Imagens: fundo1.png, bola.png, barra01.png, barra02.png
Sons: bounce.wav, gol.wav
```
```Esse é o conteúdo completo do jogo Pong implementado com JavaScript e p5.js.
https://editor.p5js.org/guilherme.silveira/sketches/htTwrazoZ
```
