# Il mio Calendario — Passo 1

Prima base di un'app calendario nativa per Android (Kotlin + Jetpack Compose).
Questo Passo 1 serve a verificare che la "catena di build" funzioni e che l'app si installi
sul telefono. Le funzioni complete arrivano ai passi successivi.

## Cosa fa questa versione
- Vista mese, navigabile avanti/indietro
- Selezione del giorno
- Aggiunta di un evento (titolo + ora) e cancellazione
- I dati vengono salvati sul telefono (file interno), quindi restano dopo la chiusura

## Cosa NON fa ancora (prossimi passi)
- Notifiche/promemoria personalizzabili (come Google Calendar)
- Eventi ricorrenti, viste settimana/giorno, ricerca
- Import da Google Calendar (file .ics)
- Sincronizzazione e backup sul Raspberry Pi

---

## Come ottenere l'APK — Metodo A: build automatica su GitHub (senza computer/Android Studio)

1. Crea un account gratuito su https://github.com e crea un nuovo repository vuoto.
2. Carica **tutto il contenuto di questa cartella** nel repository, mantenendo la struttura
   (incluse le cartelle `app/` e `.github/`). Da browser: "Add file" → "Upload files".
3. Apri la scheda **Actions** del repository. La build "Build APK" parte da sola dopo il caricamento
   (oppure avviala a mano con "Run workflow").
4. Quando la build è verde, aprila e scarica l'artifact **MyCalendar-APK** (è uno zip che contiene
   `app-debug.apk`).
5. Copia `app-debug.apk` sul telefono e installalo. La prima volta Android chiederà di consentire
   l'installazione da "app sconosciute": accetta solo per questa operazione.

> È un APK "debug", firmato con la chiave di test: va benissimo per installarlo sul tuo telefono.
> Per una firma di rilascio (Play Store o distribuzione seria) la aggiungeremo più avanti.

## Come ottenere l'APK — Metodo B: Android Studio (se hai un computer)

1. Installa Android Studio.
2. `File` → `Open` e seleziona questa cartella.
3. Attendi la sincronizzazione Gradle, collega il telefono (o usa un emulatore) e premi **Run** (▶).
   In alternativa: `Build` → `Build Bundle(s) / APK(s)` → `Build APK(s)`.

---

## Se la prima build dà errore
Copia il log della build (in GitHub: la parte rossa dello step "Build debug APK") e incollamelo:
lo sistemo. È normale che la primissima build richieda una piccola correzione.

## Versioni usate
- Android Gradle Plugin 8.5.2, Gradle 8.7, Kotlin 1.9.24
- Compose BOM 2024.06.00, Compose compiler 1.5.14
- compileSdk 34, minSdk 26 (Android 8.0+)
