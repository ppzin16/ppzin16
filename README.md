<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Seleção de produtos</title>
    <style>
        body {
            font-family: Arial, Helvetica, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

        h2 {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px;
            margin: 0;
        }

        .container {
            display: flex;
            flex-wrap: wrap;
            padding: 20px;
            justify-content: space-between;
        }

        .produto-container {
            width: calc(50% - 20px);
            margin: 10px;
            padding: 10px;
            background-color: #fff;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }

        .produto-container img {
            width: 100px;
            height: 100px;
            cursor: pointer;
        }

        p {
            margin: 10px 0;
        }

        .quantidade {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            background-color: #f0f0f0;
            border-radius: 5px;
        }

        .quantidade input {
            width: 40px;
            text-align: center;
        }

        #notaFiscal {
            list-style: none;
            padding: 0;
        }

        #notaFiscal li {
            margin: 5px 0;
        }

        #total {
            font-weight: bold;
        }

        .nota-fiscal {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: #fff;
            padding: 10px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }

        .finalizar-compra {
            text-align: center;
            margin: 20px auto;
        }

        .finalizar-compra button {
            background-color: #084e31;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .finalizar-compra button:disabled {
            background-color: #084e31;
            cursor: not-allowed;
        }
    </style>
</head>
<body>
    <h2>Selecione os Produtos:</h2>
    <div class="container">
        <div class="produto-container">
            <img src="download (9).jpg" onclick="selecionarProduto('Doritos', 3.99)">
            <p>Doritos</p>
            <div class="quantidade">
                <label>Quantidade:</label>
                <input type="number" id="quantidadeDoritos" value="1">
            </div>
        </div>
        <div class="produto-container">
            <img src="download (1).jpg" onclick="selecionarProduto('Pepsi', 2.49)">
            <p>Pepsi</p>
            <div class="quantidade">
                <label>Quantidade:</label>
                <input type="number" id="quantidadePepsi" value="1">
            </div>
        </div>
    </div>

    <div class="container">
        <div class="produto-container">
            <img src="download.jpg" onclick="selecionarProduto('Pringles', 4.99)">
            <p>Pringles</p>
            <div class="quantidade">
                <label>Quantidade:</label>
                <input type="number" id="quantidadePringles" value="1">
            </div>
        </div>
        <div class="produto-container">
            <img src="download (3).jpg" onclick="selecionarProduto('Coca Cola', 4.99)">
            <p>Coca Cola</p>
            <div class="quantidade">
                <label>Quantidade:</label>
                <input type="number" id="quantidadeCoca Cola" value="1">
            </div>
        </div>
    </div>

    <div class="container">
        <div class="produto-container">
            <img src="download (5).jpg" onclick="selecionarProduto('Cheetos', 7.49)">
            <p>Cheetos</p>
            <div class="quantidade">
                <label>Quantidade:</label>
                <input type="number" id="quantidadeCheetos" value="1">
            </div>
        </div>
        <div class="produto-container">
            <img src="download (6).jpg" onclick="selecionarProduto('Guaraviton', 5.99)">
            <p>Guaraviton</p>
            <div class="quantidade">
                <label>Quantidade:</label>
                <input type="number" id="quantidadeGuaraviton" value="1">
            </div>
        </div>
    </div>

    <div class="nota-fiscal">
        <h3>Nota Fiscal:</h3>
        <ul id="notaFiscal">
            <!-- Os produtos selecionados serão exibidos aqui -->
        </ul>
        <p><strong>Total: R$ <span id="total">0,00</span></strong></p>
        <p><strong id="mensagemCompra" style="display: none;">Compra Finalizada!</strong></p>
        <div class="finalizar-compra">
            <button onclick="finalizarCompra()" id="btnFinalizarCompra" disabled>Finalizar Compra</button>
        </div>
    </div>

    <script>
        let totalCompra = 0;

        function selecionarProduto(produto, preco) {
            const quantidadeInput = document.getElementById(`quantidade${produto}`);
            const quantidade = parseInt(quantidadeInput.value);

            if (quantidade > 0) {
                const valorProduto = quantidade * preco;
                totalCompra += valorProduto;

                const itemNota = document.createElement('li');
                itemNota.textContent = `${produto}: ${quantidade} x R$${preco.toFixed(2).replace('.', ',')} = R$${valorProduto.toFixed(2).replace('.', ',')}`;
                document.getElementById('notaFiscal').appendChild(itemNota);

                document.getElementById('total').innerText = 'R$ ' + totalCompra.toFixed(2).replace('.', ',');
                document.getElementById('btnFinalizarCompra').removeAttribute('disabled');
            } else {
                alert('Quantidade inválida. Por favor, insira um número válido.');
                quantidadeInput.value = 1;
            }
        }

        function finalizarCompra() {
            if (totalCompra > 0) {
                document.getElementById('mensagemCompra').style.display = 'block';
                document.getElementById('btnFinalizarCompra').style.display = 'none';
            }
        }
    </script>
</body>
</html>
