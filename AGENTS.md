# Hermes T3 Control

> The Czech block below is the maintainer's internal agent standard; external contributors may
> skip its reporting and review items.

<!-- agents-standard:start v1 -->
## Standardní pravidla (v1)
Kanonická verze je `AGENTS-STANDARD.md` v repu `thetedotgg/projects-meta`; tento blok neuprav lokálně.
Platí pro každé zadání, i když ho zadání neopakuje. Při rozporu má přednost pravidlo z části
„Projektová pravidla“; uplatněný rozpor uveď v bodě 5 reportu.

### Začátek úkolu
- Nejdřív vypiš, co máš k dispozici (CLI, přihlášení, klíče, MCP, prohlížeč, zařízení, přístup
  na server) a co pro úkol chybí; u klíčů a tajemství jen název a dostupnost, nikdy hodnotu.
  Chybějící přístup nenahrazuj odhadem ani simulací.

### Nic nezahazovat
- Nemaž ani nepřepisuj necommitnuté změny, cizí práci, worktrees, větve ani data. Bez výslovného
  pokynu žádný force-push, `reset --hard`, `stash`, `clean`, přepis historie ani mazání větví;
  souběžnou práci izoluj v novém worktree.
- Tajemství, klíče a klientská data nepatří do kódu, commitů, logů, screenshotů ani reportu.

### Jen se schválením uživatele
- Zveřejnění repa nebo změna jeho viditelnosti, změny DNS, produkční nasazení, nahrání do obchodů
  (Google Play, App Store a podobné), platby a placené objednávky.
- Commit a push jen když je povoluje zadání nebo projektové pravidlo; jinak změny jen připrav a popiš.
- Má-li projekt nasazení nebo vydání, doveď změnu do stavu „nasazení jedním krokem“ (jeden příkaz,
  skript nebo kliknutí). Ten krok napiš do bodu 4 reportu a neproveď ho bez schválení.

### Weby
Platí pro projekty s webovým rozhraním; jinde se neuplatní a nehlásí se jako rozpor.
- Čeština i angličtina s přirozeným textem v obou jazycích (žádný strojový překlad); texty,
  metadata a přístupné popisky v obou jazycích ve stejné změně.
- Rychlé i na starších telefonech: malé bundly, líné načítání médií, ověření na zpomaleném CPU
  a síti. Rychlost neřeš ořezáním designu.
- Před předáním dodej náhledy (screenshoty) pro mobil i desktop; odkazy na ně dej do bodu 3 reportu.

### Před PR
- Před otevřením PR nebo předáním změny k PR (nebo před pushem do hlavní větve tam, kde se PR nepoužívá) nech diff posoudit modelem
  Fable; v Claude Code je to read-only subagent `ts-advisor`. Nálezy oprav nebo uveď v bodě 5.
  Když Fable není dostupný, review nepředstírej a napiš to do bodu 6.

### Závěrečný report (česky)
Vždy v tomto pořadí; krátké odrážky, prázdný bod = „nic“, odkazy jako cesty nebo URL:
1) Hotovo · 2) Výsledky kontrol (testy, lint, typecheck, build, QA s výsledkem; nespuštěné označ) ·
3) Odkazy (soubory, náhledy, PR, preview URL) · 4) Co schválit (včetně kroku nasazení) ·
5) Rizika (včetně uplatněných rozporů se standardem) · 6) Co chybělo v zadání nebo prostředí.
<!-- agents-standard:end -->

## Projektová pravidla

Veřejný plugin pro Hermes (Python, licence MIT), který umožňuje sledovat a řídit úlohy T3 z Hermes:
nástroje `t3_threads`, `t3_thread_create`, `t3_thread_send` a další (`plugin.yaml`).
Aktuální verze je v `plugin.yaml`, podporované verze Hermes v `README.md`. Závislost `websockets>=15,<16`.

Kontroly podle `.github/workflows/ci.yml`: testy `python -B -m unittest discover -s tests -v`
s `PYTHONWARNINGS=error`; deterministický release balíček `python -B scripts/build_release.py --output-dir dist`
a ověření `python -B scripts/verify_release.py <soubor>.sha256`; kontrolní součty vydání v `release/`.
Dokumentace: `docs/operations.md`, `docs/compatibility.md`, `docs/tools.md`, `docs/security.md`,
`docs/experimental-continuation.md`; změny v `CHANGELOG.md`. Repo je veřejné: žádné interní
hostitele, absolutní domovské cesty, jména klientů ani tajemství.
