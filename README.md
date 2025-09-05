<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title id="site-title">Polimento de Faróis Premium</title>
  <style>
    :root{
      --color-bg:#f5f5f7; --color-text:#1d1d1f; --color-subtext:#6e6e73;
      --color-accent:#0071e3; --color-white:#ffffff; --color-border:#d2d2d7;
    }
    *{box-sizing:border-box}
    body{
      margin:0;font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Ubuntu,"Open Sans","Helvetica Neue",sans-serif;
      background:var(--color-bg);color:var(--color-text);line-height:1.5;
    }
    a{color:var(--color-accent);text-decoration:none}
    header{background:var(--color-white);padding:2rem 1.5rem;border-bottom:1px solid var(--color-border);text-align:center}
    header h1{font-weight:600;font-size:2.25rem;margin:0}
    main{max-width:900px;margin:3rem auto 5rem;padding:0 1.5rem}
    .intro{text-align:center;margin-bottom:3rem}
    .intro h2{font-weight:600;font-size:1.75rem;margin-bottom:.5rem}
    .intro p{font-size:1.125rem;color:var(--color-subtext);max-width:600px;margin:0 auto}
    .price{font-size:2rem;font-weight:700;color:var(--color-accent);margin-top:1rem}
    .comparison{display:flex;flex-wrap:wrap;gap:2rem;justify-content:center;margin-bottom:4rem}
    .comparison-item{background:var(--color-white);border-radius:14px;box-shadow:0 8px 24px rgb(0 0 0 / 0.1);overflow:hidden;max-width:420px;width:100%;display:flex;flex-direction:column}
    .comparison-item img{width:100%;height:auto;display:block}
    .caption{padding:1rem 1.5rem;font-weight:600;font-size:1.125rem;color:var(--color-text);background:var(--color-bg);text-align:center}
    .contact{background:var(--color-white);border-radius:14px;padding:2rem 1.5rem;box-shadow:0 8px 24px rgb(0 0 0 / 0.1);max-width:600px;margin:0 auto 3rem;text-align:center}
    .contact h3{font-weight:600;font-size:1.5rem;margin-bottom:1rem}
    footer{text-align:center;padding:1.5rem 1rem;font-size:.9rem;color:var(--color-subtext)}
    @media (max-width:600px){.comparison{flex-direction:column;align-items:center}}
    /* small helper */
    .edit-hint{font-size:.9rem;color:var(--color-subtext);margin-top:.5rem}
  </style>
</head>
<body>
  <header>
    <h1 id="brand">Polimento de Faróis Premium</h1>
    <div class="edit-hint">Conteúdo editável em <code>data.json</code></div>
  </header>

  <main>
    <section class="intro" aria-label="Introdução ao serviço">
      <h2 id="headline">Deixe seus faróis como novos</h2>
      <p id="description">Serviço profissional de polimento de faróis para restaurar a transparência, melhorar a visibilidade e valorizar seu veículo.</p>
      <p id="price" class="price">Preço: 30 euros por farol</p>
    </section>

    <section class="comparison" aria-label="Comparação antes e depois do polimento">
      <article class="comparison-item">
        <img id="img-before" src="images/farol-antes.jpg" alt="Farol antes do polimento" />
        <div class="caption" id="caption-before">Antes</div>
      </article>
      <article class="comparison-item">
        <img id="img-after" src="images/farol-depois.jpg" alt="Farol depois do polimento" />
        <div class="caption" id="caption-after">Depois</div>
      </article>
    </section>

    <section class="contact" aria-label="Informações de contato">
      <h3 id="contact-title">Contato</h3>
      <p id="email">Email: contato@polimentofarois.com</p>
      <p id="phone">Telefone: +55 11 99999-9999</p>
      <p class="edit-hint">Edite <code>data.json</code> no repositório para atualizar estes dados.</p>
    </section>
  </main>

  <footer id="footer">&copy; <span id="year">2025</span> Polimento de Faróis Premium. Todos os direitos reservados.</footer>

  <script>
    // Carrega conteúdo de data.json (editável)
    async function loadData(){
      try{
        const res = await fetch('data.json', { cache: "no-store" });
        if(!res.ok) throw new Error('Falha ao carregar data.json: ' + res.status);
        const data = await res.json();

        // Aplica ao DOM (valores fallback mantêm compatibilidade com versão anterior)
        document.title = data.siteTitle || document.title;
        document.getElementById('brand').textContent = data.siteTitle || 'Polimento de Faróis Premium';
        document.getElementById('headline').textContent = data.headline || '';
        document.getElementById('description').textContent = data.description || '';
        document.getElementById('price').textContent = (data.priceText ? data.priceText : '') || '';
        document.getElementById('img-before').src = data.images?.before || 'images/farol-antes.jpg';
        document.getElementById('img-before').alt = data.images?.beforeAlt || 'Farol antes do polimento';
        document.getElementById('caption-before').textContent = data.captions?.before || 'Antes';
        document.getElementById('img-after').src = data.images?.after || 'images/farol-depois.jpg';
        document.getElementById('img-after').alt = data.images?.afterAlt || 'Farol depois do polimento';
        document.getElementById('caption-after').textContent = data.captions?.after || 'Depois';
        document.getElementById('contact-title').textContent = data.contact?.title || 'Contato';
        document.getElementById('email').textContent = 'Email: ' + (data.contact?.email || '');
        document.getElementById('phone').textContent = 'Telefone: ' + (data.contact?.phone || '');
        document.getElementById('year').textContent = data.footerYear || new Date().getFullYear();
      }catch(err){
        console.error(err);
      }
    }
    loadData();
  </script>
</body>
</html>
