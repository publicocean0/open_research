# Open Research — Cristian Lorenzetto

Ricerca indipendente e aperta su **modelli economici** e **sistemi di decisione democratica**.
Ogni lavoro è pubblicato liberamente con il paper (italiano e inglese), le dimostrazioni matematiche,
il codice delle simulazioni e i risultati, così che chiunque possa verificarlo, riprodurlo e svilupparlo.

**Autore:** Cristian Lorenzetto, ricercatore indipendente · Padova, Italia ·
ORCID [0009-0001-4925-4728](https://orcid.org/0009-0001-4925-4728)

*An English summary is at the [end of this page](#english-summary).*

---

## Contenuto del repository

```
README.md                    questa pagina
modelli-teps-bca-dpa.zip     tutto il materiale: paper, sorgenti, figure, codice e risultati
```

Per usarlo: scarica [`modelli-teps-bca-dpa.zip`](modelli-teps-bca-dpa.zip) (pulsante *Download raw file*)
ed estrailo. I paper in PDF si leggono anche direttamente su Zenodo dai link qui sotto.

---

## Filoni di ricerca

### 1. Economia: nuovi assetti per moneta, credito e produzione

| Modello | Idea centrale | Paper |
|---|---|---|
| **TEPS — Teoria dell'Equilibrio Economico Post-Salariale** · v1.5 | Un'economia in cui la produzione è automatizzata e il lavoro umano non serve più alla produzione ordinaria. Il capitale produttivo è in un fondo pubblico, i beni essenziali sono garantiti in natura, il consumo discrezionale passa per i prezzi e il reddito civico è proporzionale alla partecipazione alle decisioni. Unisce un blocco fisico input-output, un blocco monetario stock-flow consistente, prezzi e razionamento, una matrice del capitale e un sistema di incentivi. **21 proposizioni dimostrate, 10 risultati numerici, 8 condizioni di coerenza esplicite.** | [IT](https://doi.org/10.5281/zenodo.23880578) · [EN](https://doi.org/10.5281/zenodo.23881220) |
| **BCA — Economia di mercato con Banca Centrale Algoritmica** · v1.0 | L'economia di mercato attuale, con una sola differenza: non esistono banche private. Un'unica banca centrale pubblica, con regole deterministiche eseguite da più sistemi di IA indipendenti, tiene tutti i conti e concede il credito a un tasso pubblico algoritmico senza margine di profitto. Le corse agli sportelli diventano impossibili, gli utili bancari diventano entrate pubbliche e nelle simulazioni le crisi del credito sono molto meno gravi. **16 proposizioni dimostrate, 3 risultati numerici, 7 condizioni esplicite.** | [IT](https://doi.org/10.5281/zenodo.23880939) · [EN](https://doi.org/10.5281/zenodo.23881186) |

Collegato a questo filone, su Zenodo: *Limiti strutturali del capitalismo contemporaneo*, sedici vulnerabilità strutturali formulate come proposizioni e controesempi matematici ([IT](https://doi.org/10.5281/zenodo.24078764) · [EN](https://doi.org/10.5281/zenodo.24079565)).

### 2. Decisione democratica: competenza, partecipazione e apprendimento

| Modello | Idea centrale | Paper |
|---|---|---|
| **DPA — Democrazia Ponderata Adattiva** · v1.0 | Una **rete neurale collettiva per le decisioni democratiche**: le persone sono le unità, le competenze certificate per tema sono i pesi, l'errore rispetto ai limiti reali torna indietro come proposta di correzione e il rivoto è l'aggiornamento. Su ogni tema vota chi supera una soglia di competenza, riconosciuta da formazione ed esperienza e certificata da più agenti IA indipendenti. Il peso ha un tetto, la base di voto ha un minimo che si allarga da sola, e i diritti universali restano a voto eguale. **10 proposizioni dimostrate, 7 risultati numerici, 7 condizioni esplicite**, messi alla prova contro esperti corrotti, lobby che ingannano gli agenti IA, shock, conflitti di interesse e conoscenza contro interesse. | [IT](https://doi.org/10.5281/zenodo.24100807) · [EN](https://doi.org/10.5281/zenodo.24100875) |

---

## Che cosa c'è nello zip

```
modelli-teps-bca-dpa/
├── README.md                        guida al materiale
├── LICENZA.md                       licenze (CC BY 4.0 per i documenti, MIT per il codice)
├── teps/                            TEPS: paper in pdf/ e word/ (IT, EN), testi sorgente, figure, simulazioni
├── bca/                             BCA:  paper in pdf/ e word/ (IT, EN), testi sorgente, figure, simulazioni
├── dpa/                             DPA:  paper in pdf/ e word/ (IT, EN), testi sorgente, figure
├── democrazia-ponderata-adattiva/   codice, test e risultati delle simulazioni della DPA (V0–V16, V21–V27),
│                                    con il percorso versione per versione (README.md) e lo stato dei risultati (STATO_DPA.md)
└── strumenti/                       generatori dei documenti Word e PDF
```

Ogni cartella ha un proprio README con la struttura dei file e i comandi per riprodurre i risultati.

## Metodo

- **Modello matematico prima di tutto.** Ogni lavoro definisce istituzioni, regole e ipotesi in modo
  esplicito e dimostra le proprietà principali (proposizioni D-1, D-2, …).
- **Simulazione come banco di prova.** I modelli partono da mondi interamente simulati, con parametri
  dimostrativi, e vengono messi alla prova in più scenari: shock, manipolazione, errori di misura,
  conflitti di interesse. Le esecuzioni sono deterministiche, con semi fissati, intervalli bootstrap e
  test automatici.
- **Limiti dichiarati.** Ogni paper elenca le condizioni sotto cui il modello è coerente e ciò che
  *non* è dimostrato. Gli errori trovati lungo il percorso sono corretti in versioni nuove e
  documentati, senza riscrivere le precedenti.
- **Passo successivo.** Calibrazione su dati reali e casi pilota piccoli e delimitati.

I risultati numerici sono sintetici: mostrano che cosa i modelli implicano, non provano come si
comporterebbero economie o istituzioni reali.

## Riprodurre i risultati

```bash
unzip modelli-teps-bca-dpa.zip && cd modelli-teps-bca-dpa
python3 -m pip install -r democrazia-ponderata-adattiva/requirements.txt pytest   # NumPy, SciPy, Matplotlib, pytest

# esempi
(cd bca  && python3 simulazioni/bca_1_0_registro.py)                       # registro della BCA (N-1)
(cd teps && python3 simulazioni/teps_1_5_partecipazione.py)                # TEPS, partecipazione variabile (N-10)
(cd democrazia-ponderata-adattiva/v27_dpa_conoscenza_interesse && python3 -m pytest -q)

# rigenerare tutti i paper (richiede pandoc, lxml e LibreOffice)
bash strumenti/genera_documenti.sh
```

## Collaborare

Questi lavori sono pensati come **punti di partenza per nuovi filoni di ricerca**. Sono particolarmente
benvenuti:

- verifiche indipendenti delle dimostrazioni e del codice;
- versioni dei modelli in simulazioni ad agenti tarate su dati reali;
- analisi del comportamento strategico (coalizioni, manipolazione) nella DPA;
- tesi di laurea o di dottorato e casi pilota piccoli e delimitati.

Per segnalazioni, domande o proposte di collaborazione apri una *issue* in questo repository.

## Come citare

Cita il paper su Zenodo che usi, per esempio:

> Lorenzetto, C. (2026). *DPA — Democrazia Ponderata Adattiva* (versione 1.0). Zenodo.
> https://doi.org/10.5281/zenodo.24100807

> Lorenzetto, C. (2026). *TEPS — Teoria dell'Equilibrio Economico Post-Salariale* (versione 1.5). Zenodo.
> https://doi.org/10.5281/zenodo.23880578

> Lorenzetto, C. (2026). *BCA — Economia di mercato con Banca Centrale Algoritmica* (versione 1.0). Zenodo.
> https://doi.org/10.5281/zenodo.23880939

## Licenza

Documenti (testi, Word, PDF, figure): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Codice: MIT. Il testo completo è in `LICENZA.md`, dentro lo zip.

---

## English summary

Independent, open research by **Cristian Lorenzetto** (Padova, Italy ·
ORCID [0009-0001-4925-4728](https://orcid.org/0009-0001-4925-4728)) on economic models and democratic
decision-making. All material (papers in Italian and English, sources, figures, simulation code and
results) is in [`modelli-teps-bca-dpa.zip`](modelli-teps-bca-dpa.zip).

- **TEPS — Theory of Post-Wage Economic Equilibrium** ([paper](https://doi.org/10.5281/zenodo.23881220)):
  a fully automated economy with publicly owned productive capital, an essential basket in kind and a
  civic income proportional to participation in decisions. 21 proved propositions, 10 numerical results.
- **BCA — Market Economy with an Algorithmic Central Bank** ([paper](https://doi.org/10.5281/zenodo.23881186)):
  today's market economy without private banks; a single public bank, run by independent AI systems under
  deterministic public rules, holds all accounts and lends at an algorithmic public rate with no profit
  margin. 16 proved propositions, 3 numerical results.
- **DPA — Adaptive Weighted Democracy** ([paper](https://doi.org/10.5281/zenodo.24100875)):
  a collective neural network for democratic decisions. People are the units, competences certified per
  issue are the weights, and errors against real limits flow back as correction proposals that people
  vote on. Capped weights, a minimum voting base that widens automatically, and an equal vote on universal
  rights. 10 proved propositions, 7 numerical results, tested against corrupt experts, lobbies deceiving
  the AI agents, shocks and conflicts of interest.

All numerical results come from simulated worlds with illustrative parameters: they show what the models
imply, not how real economies or institutions would behave. Contributions, independent checks, agent-based
or data-calibrated versions, theses and small pilot studies are welcome: please open an issue.

Documents are licensed CC BY 4.0, code MIT.
