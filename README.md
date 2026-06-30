<!DOCTYPE html>
<html lang="pt-br">

<head>
    <meta charset="UTF-8">
    <title>Sabor & Receita</title>

    <style>
        body{
            font-family: Arial;
            margin:0;
            background:#fff6ee;
        }

        header{
            background:#ff6b35;
            color:white;
            text-align:center;
            padding:20px;
        }

        nav button{
            margin:5px;
            padding:8px 12px;
            border:none;
            border-radius:8px;
            cursor:pointer;
        }

        main{
            max-width:900px;
            margin:auto;
            padding:20px;
        }

        .card{
            background:white;
            padding:15px;
            margin:15px 0;
            border-radius:12px;
            box-shadow:0 4px 10px rgba(0,0,0,0.1);
        }

        button{
            cursor:pointer;
            margin:5px;
        }

        .star{
            cursor:pointer;
            font-size:20px;
        }

        .hidden{
            display:none;
        }

    </style>
</head>

<body>

<header>
    <h1>🍳 Sabor & Receita</h1>

    <input id="search" placeholder="Buscar receita...">

    <nav>
        <button onclick="filtrar('todos')">Todos</button>
        <button onclick="filtrar('pizza')">🍕 Pizza</button>
        <button onclick="filtrar('hamburguer')">🍔 Hambúrguer</button>
        <button onclick="filtrar('salada')">🥗 Salada</button>
        <button onclick="filtrar('doce')">🍰 Doces</button>
    </nav>
</header>

<main>

<!-- PIZZA -->
<div class="card receita pizza">
    <h2>🍕 Pizza Artesanal</h2>

    <p>Por: Marcelo</p>

    <p>Massa leve com queijo derretido.</p>

    <div>
        ⭐ Avaliação:
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
    </div>

    <button onclick="curtir(this)">❤️ <span>0</span></button>
    <button onclick="gostar(this)">👍 <span>0</span></button>

    <div>
        <h4>Comentários</h4>
        <input placeholder="Escreva..." onkeydown="comentar(event,this)">
        <div class="comentarios"></div>
    </div>
</div>

<!-- HAMBURGUER -->
<div class="card receita hamburguer">
    <h2>🍔 Hambúrguer Artesanal</h2>

    <p>Carne suculenta e queijo cheddar.</p>

    <div>
        ⭐ Avaliação:
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
    </div>

    <button onclick="curtir(this)">❤️ <span>0</span></button>
    <button onclick="gostar(this)">👍 <span>0</span></button>

    <div>
        <h4>Comentários</h4>
        <input placeholder="Escreva..." onkeydown="comentar(event,this)">
        <div class="comentarios"></div>
    </div>
</div>

<!-- SALADA -->
<div class="card receita salada">
    <h2>🥗 Salada Mediterrânea</h2>

    <p>Leve e saudável.</p>

    <div>
        ⭐ Avaliação:
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
    </div>

    <button onclick="curtir(this)">❤️ <span>0</span></button>
    <button onclick="gostar(this)">👍 <span>0</span></button>

    <div>
        <h4>Comentários</h4>
        <input placeholder="Escreva..." onkeydown="comentar(event,this)">
        <div class="comentarios"></div>
    </div>
</div>

<!-- DOCE -->
<div class="card receita doce">
    <h2>🍰 Bolo de Chocolate</h2>

    <p>Fofinho com cobertura cremosa.</p>

    <div>
        ⭐ Avaliação:
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
        <span class="star" onclick="avaliar(this)">☆</span>
    </div>

    <button onclick="curtir(this)">❤️ <span>0</span></button>
    <button onclick="gostar(this)">👍 <span>0</span></button>

    <div>
        <h4>Comentários</h4>
        <input placeholder="Escreva..." onkeydown="comentar(event,this)">
        <div class="comentarios"></div>
    </div>
</div>

</main>

<script>

// CURTIR
function curtir(btn){
    let span = btn.querySelector("span");
    span.textContent++;
}

// GOSTEI
function gostar(btn){
    let span = btn.querySelector("span");
    span.textContent++;
}

// FILTRO
function filtrar(tipo){
    let receitas = document.querySelectorAll(".receita");

    receitas.forEach(r => {
        if(tipo === "todos"){
            r.style.display = "block";
        }else{
            r.style.display = r.classList.contains(tipo) ? "block" : "none";
        }
    });
}

// BUSCA
document.getElementById("search").addEventListener("input", function(){
    let valor = this.value.toLowerCase();

    document.querySelectorAll(".receita").forEach(r => {
        r.style.display = r.innerText.toLowerCase().includes(valor)
        ? "block"
        : "none";
    });
});

// AVALIAÇÃO
function avaliar(el){
    let estrelas = el.parentNode.querySelectorAll(".star");
    let clicado = false;

    estrelas.forEach((e,i) => {
        if(e === el) clicado = i+1;
    });

    estrelas.forEach((e,i) => {
        e.textContent = i < clicado ? "★" : "☆";
    });
}

// COMENTÁRIOS
function comentar(event,input){
    if(event.key === "Enter"){
        let div = input.nextElementSibling;

        let p = document.createElement("p");
        p.textContent = input.value;

        div.appendChild(p);

        input.value = "";
    }
}

</script>

</body>
</html>
