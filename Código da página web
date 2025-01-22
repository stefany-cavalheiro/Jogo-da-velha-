<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Jogo da Velha</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 0;
      padding: 0;
      background-color: #f4f4f4;
    }
    h1 {
      color: #333;
    }
    .board {
      display: grid;
      grid-template-columns: repeat(3, 100px);
      grid-gap: 5px;
      justify-content: center;
      margin: 20px auto;
    }
    .cell {
      width: 100px;
      height: 100px;
      background-color: #fff;
      border: 2px solid #333;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2em;
      font-weight: bold;
      cursor: pointer;
    }
    .cell.disabled {
      pointer-events: none;
      color: #aaa;
    }
    #status {
      margin: 20px;
      font-size: 1.2em;
    }
    button {
      padding: 10px 20px;
      font-size: 1em;
      background-color: #333;
      color: #fff;
      border: none;
      cursor: pointer;
      margin-top: 20px;
    }
    button:hover {
      background-color: #555;
    }
  </style>
</head>
<body>

<h1>Jogo da Velha</h1>
<div id="status">Vez do jogador: X</div>
<div class="board" id="board"></div>
<button onclick="resetGame()">Reiniciar Jogo</button>

<script>
  const board = document.getElementById('board');
  const status = document.getElementById('status');
  let currentPlayer = 'X';
  let cells = Array(9).fill('');

  function createBoard() {
    board.innerHTML = '';
    cells.forEach((cell, index) => {
      const cellDiv = document.createElement('div');
      cellDiv.classList.add('cell');
      cellDiv.textContent = cell;
      cellDiv.addEventListener('click', () => handleMove(index));
      board.appendChild(cellDiv);
    });
  }

  function handleMove(index) {
    if (cells[index] || checkWinner()) return;

    cells[index] = currentPlayer;
    currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
    status.textContent = checkWinner() ? `Jogador ${checkWinner()} venceu!` : `Vez do jogador: ${currentPlayer}`;
    if (!cells.includes('') && !checkWinner()) {
      status.textContent = 'O jogo terminou em empate!';
    }
    createBoard();
  }

  function checkWinner() {
    const winningCombinations = [
      [0, 1, 2], [3, 4, 5], [6, 7, 8],
      [0, 3, 6], [1, 4, 7], [2, 5, 8],
      [0, 4, 8], [2, 4, 6]
    ];

    for (const combination of winningCombinations) {
      const [a, b, c] = combination;
      if (cells[a] && cells[a] === cells[b] && cells[a] === cells[c]) {
        return cells[a];
      }
    }
    return null;
  }

  function resetGame() {
    cells = Array(9).fill('');
    currentPlayer = 'X';
    status.textContent = `Vez do jogador: ${currentPlayer}`;
    createBoard();
  }

  createBoard();
</script>

</body>
</html>
