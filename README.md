<!DOCTYPE html>
<html lang="ro">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Schola Latina</title>
    <style>
        body {
            background-color: #1a1a2e;
            color: #ffffff;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 15px;
        }

        .header {
            text-align: center;
            background: #16213e;
            padding: 15px;
            border-radius: 8px;
            border: 2px solid #f39c12;
            margin-bottom: 15px;
        }

        .header h1 {
            color: #f39c12;
            margin: 0 0 5px 0;
            font-size: 1.5rem;
        }

        .nav-menu {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 20px;
        }

        .nav-btn {
            flex: 1 1 40%;
            background: #0f3460;
            color: #f39c12;
            border: 2px solid #f39c12;
            padding: 12px;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.9rem;
        }

        .nav-btn.active {
            background: #f39c12;
            color: #000;
        }

        .box {
            display: none;
            background: #16213e;
            padding: 15px;
            border-radius: 8px;
            border: 1px solid #0f3460;
        }

        .box.active {
            display: block;
        }

        .card {
            background: #0f3460;
            padding: 12px;
            border-radius: 6px;
            margin-bottom: 12px;
        }

        .card h3 {
            color: #e74c3c;
            margin-top: 0;
        }

        .clickable {
            color: #f39c12;
            font-weight: bold;
            text-decoration: underline;
            cursor: pointer;
        }

        .quiz-opt {
            display: block;
            width: 100%;
            text-align: left;
            background: #1a1a2e;
            color: #fff;
            border: 1px solid #f39c12;
            padding: 10px;
            margin: 5px 0;
            border-radius: 4px;
            cursor: pointer;
        }

        .quiz-opt.right { background: #2ecc71 !important; color: #000; font-weight: bold; }
        .quiz-opt.wrong { background: #e74c3c !important; }

        .rpg-area {
            background: #000;
            padding: 15px;
            border-radius: 6px;
            text-align: center;
            border: 1px solid #f39c12;
        }

        .btn-rpg {
            background: #f39c12;
            color: #000;
            border: none;
            padding: 8px 15px;
            font-weight: bold;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <div class="header">
        <h1>🏛️ Schola Latina</h1>
        <p>Gerunziu și Gerundiv</p>
    </div>

    <div class="nav-menu">
        <button class="nav-btn active" onclick="showTab('tab1', this)">📜 1. Lecție</button>
        <button class="nav-btn" onclick="showTab('tab2', this)">🎭 2. RPG</button>
        <button class="nav-btn" onclick="showTab('tab3', this)">🔍 3. Exemple</button>
        <button class="nav-btn" onclick="showTab('tab4', this)">⚔️ 4. Test</button>
    </div>

    <!-- 1. LECTIE -->
    <div id="tab1" class="box active">
        <h2>📜 Regulile Gramaticale</h2>
        <br>
        <div class="card">
            <h3>1. Gerunziul (Nume Verbal Activ)</h3>
            <p>Substantiv verbal activ la declinarea a II-a.</p>
            <ul>
                <li><strong>Genitiv:</strong> <em>ars amandi</em> (arta de a iubi)</li>
                <li><strong>Acuzativ:</strong> <em>ad discendum</em> (pentru a învăța)</li>
                <li><strong>Ablativ:</strong> <em>docendo discimus</em> (învățăm predând)</li>
            </ul>
        </div>
        <div class="card">
            <h3>2. Gerundivul (Adjectiv Verbal Pasiv)</h3>
            <p>Exprimă o obligație sau necesitate.</p>
            <ul>
                <li><em>Carthago delenda est!</em> (Cartagina trebuie distrusă!)</li>
                <li><em>ad urbem defendendam</em> (pentru a apăra cetatea)</li>
            </ul>
        </div>
    </div>

    <!-- 2. RPG -->
    <div id="tab2" class="box">
        <h2>🎭 Dialog RPG</h2>
        <br>
        <div class="rpg-area">
            <div id="rpg-icon" style="font-size:2.5rem;">⚔️</div>
            <h3 id="rpg-name" style="color:#e74c3c;">MARCUS CENTURIO</h3>
            <p id="rpg-lat" style="color:#f39c12; font-size:1.1rem; font-weight:bold;">Milites! Tempus ad pugnandum venit!</p>
            <p id="rpg-ro" style="font-style:italic;">Ostași! A sosit timpul pentru a lupta!</p>
            <p id="rpg-expl" style="font-size:0.85rem; color:#2ecc71; background:#111; padding:5px;">📌 ad pugnandum = Gerunziu la Acuzativ (scopul).</p>
            <br>
            <button class="btn-rpg" onclick="stepRPG(-1)">⬅️ Înapoi</button>
            <span id="rpg-num" style="margin: 0 10px;">1 / 3</span>
            <button class="btn-rpg" onclick="stepRPG(1)">Înainte ➡️</button>
        </div>
    </div>

    <!-- 3. EXEMPLE -->
    <div id="tab3" class="box">
        <h2>🔍 Inspector de Exemple</h2>
        <p>Apasă pe cuvinte pentru explicații:</p>
        <br>
        <div class="card">
            1. Homines <span class="clickable" onclick="inspect('ad discendum', 'Gerunziu Acuzativ (scop): pentru a învăța.')">ad discendum</span> nati sunt.
        </div>
        <div class="card">
            2. Ars <span class="clickable" onclick="inspect('scribendarum epistularum', 'Sintagmă Gerundivală Genitiv: arta de a scrie scrisori.')">scribendarum epistularum</span>.
        </div>
        <div class="card">
            3. <span class="clickable" onclick="inspect('Carthago delenda est', 'Pasiv Perifrastic: Cartagina TREBUIE distrusă.')">Carthago delenda est</span>.
        </div>
        <div class="card">
            4. Mens <span class="clickable" onclick="inspect('discendo', 'Gerunziu Ablativ: prin învățare.')">discendo</span> alitur.
        </div>

        <div id="inspect-box" style="display:none; background:#000; padding:10px; border:1px solid #2ecc71; margin-top:10px;">
            <h4 id="ins-t" style="color:#f39c12; margin:0;">-</h4>
            <p id="ins-d" style="margin:5px 0 0 0;">-</p>
        </div>
    </div>

    <!-- 4. QUIZ -->
    <div id="tab4" class="box">
        <h2>⚔️ Test (XP: <span id="xp">0</span>)</h2>
        <br>
        <div class="card">
            <p><strong>1. Ce este "Ad pacem faciendam"?</strong></p>
            <button class="quiz-opt" onclick="check(this, false)">A) Gerunziu la Dativ</button>
            <button class="quiz-opt" onclick="check(this, true)">B) Sintagmă Gerundivală la Acuzativ</button>
        </div>
        <div class="card">
            <p><strong>2. Traducere: "Libri legendi sunt":</strong></p>
            <button class="quiz-opt" onclick="check(this, false)">A) Cărțile au fost citite.</button>
            <button class="quiz-opt" onclick="check(this, true)">B) Cărțile trebuie citite.</button>
        </div>
        <div class="card">
            <p><strong>3. Ce caz are "Docendo discimus"?</strong></p>
            <button class="quiz-opt" onclick="check(this, true)">A) Ablativ</button>
            <button class="quiz-opt" onclick="check(this, false)">B) Nominativ</button>
        </div>
    </div>

    <script>
        function showTab(tabId, btn) {
            document.querySelectorAll('.box').forEach(b => b.classList.remove('active'));
            document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
            document.getElementById(tabId).classList.add('active');
            btn.classList.add('active');
        }

        const rpgData = [
            { icon: "⚔️", name: "MARCUS CENTURIO", lat: "Milites! Tempus ad pugnandum venit!", ro: "Ostași! A sosit timpul pentru a lupta!", expl: "📌 ad pugnandum = Gerunziu la Acuzativ (scopul)." },
            { icon: "🏛️", name: "LIVIA ERUDITA", lat: "Ad urbem defendendam cuncti parati esse debemus!", ro: "Cu toții trebuie să fim pregătiți pentru a apăra cetatea!", expl: "📌 ad urbem defendendam = Sintagmă Gerundivală la Acuzativ." },
            { icon: "📜", name: "CASSIUS SENATOR", lat: "Carthago delenda est!", ro: "Cartagina trebuie distrusă!", expl: "📌 delenda est = Pasiv Perifrastic (Gerundiv de obligație)." }
        ];

        let rpgIdx = 0;
        function stepRPG(dir) {
            rpgIdx += dir;
            if (rpgIdx < 0) rpgIdx = 0;
            if (rpgIdx >= rpgData.length) rpgIdx = rpgData.length - 1;

            let d = rpgData[rpgIdx];
            document.getElementById('rpg-icon').innerText = d.icon;
            document.getElementById('rpg-name').innerText = d.name;
            document.getElementById('rpg-lat').innerText = d.lat;
            document.getElementById('rpg-ro').innerText = d.ro;
            document.getElementById('rpg-expl').innerText = d.expl;
            document.getElementById('rpg-num').innerText = (rpgIdx + 1) + " / " + rpgData.length;
        }

        function inspect(title, desc) {
            document.getElementById('inspect-box').style.display = 'block';
            document.getElementById('ins-t').innerText = title;
            document.getElementById('ins-d').innerText = desc;
        }

        let score = 0;
        function check(btn, isCorrect) {
            let parent = btn.parentNode;
            if (parent.dataset.done) return;
            parent.dataset.done = "true";

            if (isCorrect) {
                btn.classList.add('right');
                score += 10;
                document.getElementById('xp').innerText = score;
            } else {
                btn.classList.add('wrong');
            }
        }
    </script>
</body>
</html>
