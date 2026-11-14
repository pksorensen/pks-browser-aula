# pks-browser-aula

Browser-opskrifter til Aula, kørt **lokalt** af [Agentics browser-tray](https://agentics.dk/products/pks-agent-browser).

**[Åbn opskrifterne på agentics.dk →](https://agentics.dk/browser/recipes/pksorensen/pks-browser-aula)**

## Opskrifter

| Fil | Hvad den gør | Profil |
| --- | --- | --- |
| [`recipes/aula-connect.json`](recipes/aula-connect.json) | Forbinder Aula: du logger ind som forælder med dit eget MitID, trayen gemmer adgangen krypteret på maskinen | `aula` |

## Sådan virker `aula-connect`

Opskriften åbner Aulas eget login i et synligt Edge-vindue. **Du klikker selv** — vælger
MitID, taster dit bruger-ID og godkender i appen; der står ikke ét klik i opskriften. Når
Aula sender dig tilbage, fanger trayen login-koden og bytter den til adgang.

- **PKCE-nøglen bliver i trayen.** Browseren og opskriften ser kun en offentlig "challenge",
  så en kode fanget i browseren er ubrugelig for alle andre.
- **Adgangen fornyes én gang med det samme** som bevis på at den kan holdes i live uden MitID.
- **Den gemmes krypteret** for din Windows-bruger (DPAPI) i
  `%USERPROFILE%\.agentics\browser-tray\tokens\aula.bin`. Intet token står i resultatfilen.
- **Kun fra din egen tray.** En opskrift der fanger et login kan ikke sendes som job fra en
  platform; den kører kun når du selv trykker.

Klient-id'et i filen er Aula-appens offentlige — det samme som alle fællesskabsprojekterne
bruger. Det er ikke en hemmelighed, men det er heller ikke en aftale med Aula.

## Installér

Tryk **Installér i trayen** eller **Kør nu** på [opskriftssiden](https://agentics.dk/browser/recipes/pksorensen/pks-browser-aula).
Trayen viser en kvittering med commit, værter og aftryk, og spørger hver gang.
