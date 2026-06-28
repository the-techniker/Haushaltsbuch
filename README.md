# Haushaltsbuch

Vanilla HTML/CSS/JS PWA für iPhone, gehostet auf GitHub Pages. Backend: Google Sheets via Apps Script.

## Apps Script deployen (nach Code-Änderungen)

1. Setup-Tab in der App öffnen → **Code kopieren**
2. [script.google.com](https://script.google.com) → das verknüpfte Projekt öffnen
3. Bestehenden Code komplett ersetzen → **Speichern**
4. **Bereitstellen → Bereitstellung verwalten → Bearbeiten (Stift-Icon)**
5. Version: **Neue Version** auswählen → **Bereitstellen**
6. Die URL bleibt gleich – kein neues Eintragen nötig

> Wichtig: Immer „Neue Version" wählen, sonst bleibt der alte Code aktiv.

## Bekannte Fallstricke

**Timezone-Bug (erster Monatstag):** Google Sheets konvertiert Datumsstrings automatisch zu Date-Objekten. Apps Script serialisiert diese per UTC (`toISOString()`), was in UTC+2 den 1. eines Monats einen Tag zurückwirft. Fix: `getData()` nutzt `Utilities.formatDate(val, Session.getScriptTimeZone(), 'yyyy-MM-dd')` für alle Datum-Zellen.
