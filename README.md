# KvízMania 🎮

Kvízová hra ve stylu Kahoot. **Bez databáze, bez vlastního serveru** — celá hra je jeden soubor `index.html`.

- 🎮 **Na jednom zařízení** – 1–8 hráčů na střídačku (funguje i offline)
- 📡 **Hostit online hru** – vygeneruje se PIN + QR kód, ostatní se připojí na mobilu
- 📱 **Připojit se** – zadáš PIN (nebo naskenuješ QR) a hraješ na svém telefonu
- ✏️ Editor vlastních sad otázek (ABCD i Pravda/Lež), export/import do `.json`
- 🌙 Tmavý režim, zvuky, konfety, žebříček, sloupcový graf odpovědí

Online režim funguje přes **WebRTC (PeerJS)** — hráči se spojí přímo mezi sebou,
stav hry žije jen v prohlížeči hostitele. Žádná data se nikam neukládají.

---

## Jak to dát online (vyber jednu možnost)

> Aby šel QR kód / odkaz naskenovat z cizího mobilu, musí být stránka na internetu
> přes **https**. Z lokálního souboru (`file://`) se na ni telefon nedostane.

### A) Netlify Drop — nejrychlejší, bez účtu i bez příkazů
1. Jdi na **https://app.netlify.com/drop**
2. Přetáhni tam celou tuto složku (nebo jen `index.html`).
3. Dostaneš veřejný odkaz typu `https://nazev.netlify.app` — hotovo.

### B) GitHub Pages — trvalý odkaz, hodí se na odevzdání
1. Vytvoř repozitář na https://github.com → **New repository** (Public).
2. Nahraj `index.html` (tlačítko *Add file → Upload files*).
3. **Settings → Pages → Branch: `main` / root → Save.**
4. Za chvíli běží na `https://tvojejmeno.github.io/nazev-repa/`.

Pokud máš lokálně git (tahle složka už je připravená jako repo):
```bash
git remote add origin https://github.com/TVOJE_JMENO/kvizmania.git
git push -u origin main
```
…a pak zapni Pages podle kroku 3.

### C) Cloudflare Pages / Vercel
Stejný princip: napoj repozitář nebo přetáhni složku, je to statická stránka bez buildu.

---

## Použití ve třídě
1. Na svém počítači: **Hostit online hru** → vyber sadu → ukáže se PIN a QR.
2. Spolužáci otevřou tvůj odkaz na mobilu → **Připojit se** → naskenují QR
   nebo zadají PIN.
3. Až jsou v lobby, klikneš **Spustit hru**. Otázky se ukazují na tvé obrazovce
   (projektor), odpovídá se na telefonech.

## Technické info
- Čistě statická stránka (HTML + CSS + JS v jednom souboru).
- Externí knihovny z CDN: `peerjs` (P2P spojení) a `qrcode-generator` (QR kód).
- Otázky se ukládají v prohlížeči přes `localStorage`.
