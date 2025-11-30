<img width="1891" height="921" alt="1 2" src="https://github.com/user-attachments/assets/96a77419-675a-46fa-9ee5-2dc09e37bdcb" /><img width="1897" height="932" alt="1 1" src="https://github.com/user-attachments/assets/3ea38d89-c5f8-46e1-90cd-41a963283970" /><!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>AgriVista — Immersive Agriculture Website (HTML + CSS)</title>
  <meta name="description" content="AgriVista — large agriculture site built with HTML & CSS. Animated hero, sections for crops, livestock, marketplace, training, analytics mock, resources, contact, and CSS-only components.">
  <style>
    /* ----------------------
       Root & base
       ----------------------*/
    :root{
      --bg:#0f1724; --card:#0b1220; --muted:#94a3b8; --accent:#18a058; --accent-2:#22c55e; --glass:rgba(255,255,255,0.04);
      --glass-2:rgba(255,255,255,0.02);
      --maxw:1200px; --radius:14px; --mono: ui-monospace, SFMonaco, Menlo, Monaco, 'Roboto Mono', monospace;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,Helvetica,Arial;background:linear-gradient(180deg,#071029 0%,#071018 60%);color:#e6eef8}
    a{color:var(--accent)}
    .container{max-width:var(--maxw);margin:0 auto;padding:1rem}

    /* ----------------------
       Top Navigation
       ----------------------*/
    header{position:fixed;left:0;right:0;top:0;z-index:60;padding:0.6rem 0;backdrop-filter:blur(6px);}
    .nav-wrap{display:flex;align-items:center;justify-content:space-between;background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:0.6rem;border-radius:12px}
    .brand{display:flex;align-items:center;gap:0.8rem}
    .logo{width:44px;height:44px;border-radius:10px;background:linear-gradient(135deg,var(--accent),var(--accent-2));display:flex;align-items:center;justify-content:center;font-weight:800;color:#061017}
    nav ul{display:flex;gap:0.6rem;list-style:none;margin:0;padding:0}
    nav a{padding:0.5rem 0.8rem;border-radius:10px;color:inherit;text-decoration:none;font-weight:600}
    nav a:hover{background:var(--glass)}
    .cta{background:linear-gradient(90deg,var(--accent-2),var(--accent));padding:0.45rem 0.9rem;border-radius:12px;color:#041018;font-weight:700}

    /* ----------------------
       Hero with Parallax layers (pure CSS illusion)
       ----------------------*/
    .hero{display:grid;grid-template-columns:1fr 420px;gap:1rem;align-items:center;padding:6.5rem 0 3rem}
    .hero-left{padding-right:1rem}
    .kicker{display:inline-block;background:linear-gradient(90deg,rgba(255,255,255,0.04),rgba(255,255,255,0.02));padding:0.35rem 0.6rem;border-radius:999px;font-weight:700;font-size:0.85rem}
    h1{font-size:2.2rem;line-height:1.02;margin:0 0 0.6rem;background:linear-gradient(90deg,#ecfeee,#c7f9d4);-webkit-background-clip:text;background-clip:text;color:transparent}
    p.lead{color:var(--muted);max-width:56ch;margin-bottom:1rem}

    /* animated keywords */
    .headline-meta{display:flex;gap:0.6rem;align-items:center;flex-wrap:wrap}
    .pulse-blob{width:12px;height:12px;border-radius:50%;background:var(--accent);box-shadow:0 0 24px rgba(34,197,94,0.18);animation:blob 3s infinite}
    @keyframes blob{0%{transform:scale(1)}50%{transform:scale(1.35) translateY(-2px)}100%{transform:scale(1)}}

    /* hero right illustration card */
    .hero-card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:1rem;border-radius:16px;backdrop-filter:blur(6px);box-shadow:0 10px 40px rgba(2,6,23,0.6)}
    .hero-card .item{display:flex;align-items:center;gap:0.8rem;padding:0.5rem;border-radius:10px}

    /* animated showcase grid */
    .showcase{display:grid;grid-template-columns:repeat(3,1fr);gap:0.8rem;margin-top:1rem}
    .showcase .card{position:relative;overflow:hidden}
    .showcase .card::after{content:'';position:absolute;inset:0;background:linear-gradient(180deg,transparent,rgba(0,0,0,0.18));opacity:0;transition:opacity .35s}
    .showcase .card:hover::after{opacity:1}

    /* marquee strip */
    .marquee{overflow:hidden;border-radius:12px;padding:0.7rem;background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));margin:1rem 0}
    .marquee .track{display:inline-block;white-space:nowrap;animation:marquee 18s linear infinite}
    @keyframes marquee{0%{transform:translateX(0)}100%{transform:translateX(-50%)}}

    /* sections */
    section.card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:1.2rem;border-radius:16px;margin-bottom:1rem}
    .two-col{display:grid;grid-template-columns:2fr 1fr;gap:1rem}

    /* animated counters */
    .counters{display:flex;gap:0.8rem}
    .counter{padding:0.6rem;border-radius:12px;background:var(--glass-2);min-width:110px;text-align:center}
    .counter strong{display:block;font-size:1.25rem}

    /* CSS-only accordion (pure checkbox hack) */
    .accordion{border-radius:12px;overflow:hidden}
    .accordion input{display:none}
    .accordion label{display:block;padding:0.7rem;background:var(--glass);cursor:pointer;font-weight:700}
    .accordion .panel{max-height:0;overflow:hidden;transition:max-height .4s ease;padding:0 0.8rem}
    .accordion input:checked + label + .panel{max-height:500px;padding:0.7rem 0.8rem}

    /* animated cards with tilt & fade-in */
    .card-anim{transform:translateY(12px);opacity:0;animation:fadeUp .8s ease forwards}
    .card-anim.delay-1{animation-delay:.15s}
    .card-anim.delay-2{animation-delay:.3s}
    @keyframes fadeUp{to{transform:none;opacity:1}}

    /* gallery with CSS filters and hover zoom */
    .gallery{display:grid;grid-template-columns:repeat(4,1fr);gap:0.6rem}
    .gallery img{width:100%;height:140px;object-fit:cover;border-radius:10px;transition:transform .45s ease,filter .45s}
    .gallery img:hover{transform:scale(1.06);filter:brightness(1.05) saturate(1.1)}

    /* footer */
    footer{padding:1rem 0;color:var(--muted);margin-top:1rem}

    /* responsiveness */
    @media (max-width:1100px){.hero{grid-template-columns:1fr} .showcase{grid-template-columns:repeat(2,1fr)} .gallery{grid-template-columns:repeat(2,1fr)} }
    @media (max-width:680px){nav ul{display:none} .two-col{grid-template-columns:1fr} .showcase{grid-template-columns:1fr} .gallery{grid-template-columns:1fr} .hero{padding-top:4.5rem}}

    /* fun footer animation */
    .pulse-row{display:flex;gap:0.6rem;align-items:center}
    .leaf{width:18px;height:18px;border-radius:4px;background:linear-gradient(90deg,var(--accent),var(--accent-2));animation:leafFloat 4s ease-in-out infinite}
    @keyframes leafFloat{0%{transform:translateY(0)}50%{transform:translateY(-6px) rotate(-6deg)}100%{transform:translateY(0)}}

    /* subtle floating background shapes */
    .bg-shape{position:fixed;pointer-events:none;filter:blur(48px);opacity:0.18;z-index:0}
    .bg-1{width:420px;height:420px;right:-100px;top:-80px;background:radial-gradient(circle at 30% 30%, #0ef27a, transparent 40%)}
    .bg-2{width:320px;height:320px;left:-120px;bottom:-120px;background:radial-gradient(circle at 70% 70%, #18a058, transparent 35%)}

  </style>
</head>
<body>
  <div class="bg-shape bg-1" aria-hidden="true"></div>
  <div class="bg-shape bg-2" aria-hidden="true"></div>

  <header>
    <div class="container nav-wrap">
      <div class="brand"><div class="logo">AV</div><div style="line-height:1"><strong>AgriVista</strong><div style="font-size:0.75rem;color:var(--muted)">Grow | Learn | Trade</div></div></div>
      <nav>
        <ul>
          <li><a href="#home">Home</a></li>
          <li><a href="#crops">Crops</a></li>
          <li><a href="#market">Market</a></li>
          <li><a href="#training">Training</a></li>
          <li><a href="#community">Community</a></li>
          <li><a href="#resources">Resources</a></li>
        </ul>
      </nav>
      <div><a class="cta" href="#join">Get Started</a></div>
    </div>
  </header>

  <main class="container">
    <!-- HERO -->
    <section id="home" class="hero">
      <div class="hero-left">
        <span class="kicker">Sustainable • Smart • Local</span>
        <h1>Future-ready agriculture tools and community for farmers and agri-businesses</h1>
        <p class="lead">AgriVista brings together crop guides, marketplace, training, weather-aware recomendations, pest diagnostics and an analytics suite — all with delightful animations and a responsive HTML/CSS experience.</p>

        <div class="headline-meta" aria-hidden="false">
          <div class="pulse-blob"></div>
          <div class="muted">120+ crops</div>
          <div class="muted">•</div>
          <div class="muted">Marketplace & Logistics</div>
          <div class="muted">•</div>
          <div class="muted">LMS & Training</div>
        </div>

        <div style="margin-top:1rem;display:flex;gap:0.6rem;align-items:center">
          <input placeholder="Search crops, guides or market..." style="flex:1;padding:0.7rem;border-radius:12px;border:none;background:rgba(255,255,255,0.02);color:inherit" />
          <button class="cta">Search</button>
        </div>

        <div class="marquee" aria-hidden="true"><div class="track">🌾 New harvest listings • Subsidy updates • Free webinar: Integrated Pest Management • Regional price alerts • 🌾 New harvest listings • Subsidy updates • Free webinar: Integrated Pest Management • Regional price alerts •</div></div>

        <div class="showcase">
          <div class="card card-anim delay-1"><h4>Yield Planner</h4><p class="muted">Plan target yields and inputs with seasonal templates.</p></div>
          <div class="card card-anim delay-2"><h4>Pest Visual Guide</h4><p class="muted">Image-based CSS gallery with reference notes.</p></div>
          <div class="card card-anim"><h4>Marketplace</h4><p class="muted">List produce, accept offers and schedule logistics.</p></div>
        </div>
      </div>

      <aside class="hero-card">
        <div style="display:flex;flex-direction:column;gap:0.7rem">
          <div class="item"><strong>Live indicators</strong><div style="margin-left:auto;color:var(--muted)">Updated hourly</div></div>
          <div class="item"><div style="flex:1"><strong>Weather</strong><div class="muted">Monsoon window: 12–18 mm</div></div></div>
          <div class="item"><div style="flex:1"><strong>Price Index (Wk)</strong><div class="muted">Tomato ↑ 4.2% • Wheat ↔</div></div></div>
          <div class="item"><button style="margin-top:0.2rem;padding:0.6rem;border-radius:10px;background:linear-gradient(90deg,var(--accent-2),var(--accent));border:none;font-weight:700;color:#041018">Create Listing</button></div>
        </div>
      </aside>
    </section>

    <!-- CROPS SECTION -->
    <section id="crops" class="card">
      <h2>Crops Library</h2>
      <p class="muted">Comprehensive crop pages with CSS-driven timelines and responsive planting calendars.</p>

      <div class="two-col" style="margin-top:1rem">
        <div>
          <div style="display:grid;grid-template-columns:repeat(2,1fr);gap:0.6rem">
            <div class="card"><h4>Wheat</h4><p class="muted">Sowing: Nov–Jan</p></div>
            <div class="card"><h4>Rice</h4><p class="muted">Puddled transplanting • Water saving tips</p></div>
            <div class="card"><h4>Millets</h4><p class="muted">Drought-resilient varieties</p></div>
            <div class="card"><h4>Pulses</h4><p class="muted">N-fixing benefits</p></div>
          </div>
        </div>

        <div>
          <div class="card">
            <h4>Regional Planting Calendar</h4>
            <div style="display:flex;gap:0.6rem;flex-wrap:wrap;margin-top:0.6rem">
              <div style="background:var(--glass);padding:0.4rem 0.6rem;border-radius:999px">North</div>
              <div style="background:var(--glass);padding:0.4rem 0.6rem;border-radius:999px">Central</div>
              <div style="background:var(--glass);padding:0.4rem 0.6rem;border-radius:999px">South</div>
            </div>
            <div style="margin-top:0.8rem">
              <div class="accordion">
                <input type="checkbox" id="ac1"><label for="ac1">Wheat — Detailed schedule</label>
                <div class="panel">Soil prep → Sowing → Fertilizer at 30 & 60 days → Harvest. Use certified seed and balanced NPK.</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- MARKETPLACE -->
    <section id="market" class="card">
      <h2>Marketplace</h2>
      <p class="muted">List produce or equipment. Buyers can filter by distance, price and harvest date.</p>
      <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:0.8rem;margin-top:1rem">
        <div class="card"><h4>Tomato — 2 MT</h4><p class="muted">Price: ₹22/kg — Location: Nashik</p></div>
        <div class="card"><h4>Wheat — 8 MT</h4><p class="muted">Price: ₹2,080/qtl — Location: Karnal</p></div>
        <div class="card"><h4>Tractor — 2WD</h4><p class="muted">Used, good condition</p></div>
      </div>

      <div style="margin-top:1rem;display:flex;gap:0.8rem;align-items:center">
        <div class="counter" aria-hidden="true"><strong>4.8k</strong><div class="muted">Active Users</div></div>
        <div class="counter" aria-hidden="true"><strong>1.2k</strong><div class="muted">Listings</div></div>
        <div class="counter" aria-hidden="true"><strong>320</strong><div class="muted">Avg. weekly orders</div></div>
      </div>
    </section>

    <!-- TRAINING & LMS -->
    <section id="training" class="card">
      <h2>Training & Courses</h2>
      <p class="muted">Video lessons, printable manuals, quizzes and certificates for completion.</p>
      <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:0.6rem;margin-top:0.8rem">
        <div class="card"><strong>Intro to Soil Health</strong><p class="muted">2 lessons • 45 min</p></div>
        <div class="card"><strong>Climate-smart irrigation</strong><p class="muted">3 lessons • 60 min</p></div>
        <div class="card"><strong>Pest Management</strong><p class="muted">4 lessons • 80 min</p></div>
      </div>
    </section>

    <!-- COMMUNITY -->
    <section id="community" class="card">
      <h2>Community & Forum</h2>
      <p class="muted">Ask experts, share success stories, regional groups and event calendar.</p>
      <div style="display:flex;gap:0.8rem;margin-top:0.8rem;flex-wrap:wrap">
        <div style="padding:0.6rem;border-radius:12px;background:var(--glass);min-width:180px">Regional Group: Maharashtra</div>
        <div style="padding:0.6rem;border-radius:12px;background:var(--glass);min-width:180px">Dairy Farmers Network</div>
        <div style="padding:0.6rem;border-radius:12px;background:var(--glass);min-width:180px">Agri Startups</div>
      </div>
    </section>

    <!-- RESOURCES & GALLERY -->
    <section id="resources" class="card">
      <h2>Resources</h2>
      <p class="muted">Downloadable manuals, PDF guides, video demos and animated infographics.</p>
      <div class="gallery" style="margin-top:0.8rem">
        <img src="https://images.unsplash.com/photo-1501004318641-b39e6451bec6?q=80&w=800&auto=format&fit=crop&ixlib=rb-4.0.3&s=123" alt="Field">
        <img src="https://images.unsplash.com/photo-1541099649105-f69ad21f3246?q=80&w=800&auto=format&fit=crop&ixlib=rb-4.0.3&s=234" alt="Harvest">
        <img src="https://images.unsplash.com/photo-1601004890684-d8cbf643f5f2?q=80&w=800&auto=format&fit=crop&ixlib=rb-4.0.3&s=345" alt="Workers">
        <img src="https://images.unsplash.com/photo-1504198453319-5ce911bafcde?q=80&w=800&auto=format&fit=crop&ixlib=rb-4.0.3&s=456" alt="Crops">
      </div>
    </section>

    <!-- FAQ with CSS animation -->
    <section id="faq" class="card">
      <h2>FAQ</h2>
      <div style="display:grid;gap:0.6rem;margin-top:0.6rem">
        <div class="card" style="padding:0.8rem"><strong>How do I list a crop?</strong><p class="muted">Go to Marketplace → Create Listing → Add images, price and harvest date.</p></div>
        <div class="card" style="padding:0.8rem"><strong>Can I host training offline?</strong><p class="muted">Yes — there's an exportable PDF and certificate system for offline learners.</p></div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" class="card">
      <h2>Contact & Partnerships</h2>
      <p class="muted">For API access, partnerships and training programs.</p>
      <form style="display:grid;gap:0.6rem;margin-top:0.6rem">
        <input placeholder="Name" style="padding:0.6rem;border-radius:8px;border:none;background:rgba(255,255,255,0.02);color:inherit" />
        <input placeholder="Email or Phone" style="padding:0.6rem;border-radius:8px;border:none;background:rgba(255,255,255,0.02);color:inherit" />
        <textarea placeholder="Message" rows="4" style="padding:0.6rem;border-radius:8px;border:none;background:rgba(255,255,255,0.02);color:inherit"></textarea>
        <div style="display:flex;gap:0.6rem"><button class="cta" type="button">Send</button><button style="padding:0.6rem;border-radius:8px;background:transparent;border:1px solid var(--glass);">Clear</button></div>
      </form>
    </section>

    <!-- FOOTER -->
    <footer>
      <div style="display:flex;justify-content:space-between;align-items:center;gap:1rem;flex-wrap:wrap">
        <div><strong>AgriVista</strong><div class="muted">© 2025 AgriVista • Built with HTML & CSS</div></div>
        <div class="pulse-row"><div class="leaf"></div><div class="leaf" style="animation-delay:.3s"></div><div class="leaf" style="animation-delay:.6s"></div></div>
      </div>
    </footer>
  </main>

  <script>
    // Minimal JS: smooth scrolling for anchors
    document.querySelectorAll('a[href^="#"]').forEach(a=>{a.addEventListener('click',e=>{const t=document.querySelector(a.getAttribute('href')); if(t){e.preventDefault(); t.scrollIntoView({behavior:'smooth',block:'start'})}})});
  </script>
</body>
</html>                 <
