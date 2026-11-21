# Rang Mausam: Android weather widget

A home-screen widget that turns the forecast into a carry-list, drawn in the style of Indian folk painting.
If rain is expected in the next 12 hours you get a chhata and raincoat; snow brings boots and a jacket;
fog brings a monkey cap and muffler. The weather word is written in Hindi, Kannada, Tamil or Bengali.

- Native Android app, no Google Play Services, no extra libraries. Works on Android 8.0 and newer.
- Forecast: Open-Meteo (free, no API key, no account).
- Location: your phone's location while the app is open, or a city you type. Nothing is sent anywhere else.
- Widget is resizable: wide and short shows the medium layout, square and small shows the small one,
  big and square shows the large one with a five-day carry-list strip.

## Get the APK: option A, GitHub builds it for you (no software to install)

1. Make a free account at github.com if you do not have one.
2. Create a new repository called `rang-mausam` (Private is fine). Tick "Add a README" so it is not empty.
3. On a laptop, open the repository, choose **Add file > Upload files**, and drag in everything from this
   folder (the `app` and `gradle` folders, `gradlew`, `gradlew.bat`, `build.gradle.kts`,
   `settings.gradle.kts`, `gradle.properties`). Commit.
4. Folders whose names start with a dot are often skipped by browser upload. So add the build recipe by hand:
   **Add file > Create new file**, name it `.github/workflows/build-apk.yml`, paste in the contents of
   that file from this folder, and commit.
5. Open the **Actions** tab. A build named "Build APK" starts on its own (about 5 to 8 minutes).
   If it does not, choose "Build APK" and press **Run workflow**.
6. When it is green, open **Releases** (right-hand side of the repository page) on your phone and tap
   `RangMausam.apk` under "Rang Mausam (latest build)".

Every later change you commit rebuilds the APK automatically.

## Get the APK: option B, Android Studio

1. Install Android Studio (free) and open this folder with **File > Open**. Let it finish syncing.
2. On the phone, turn on Developer options and USB debugging, connect it by cable, and press **Run**.

## Install and set up on the phone

1. Open the downloaded `RangMausam.apk`. Android will ask to allow installs from your browser or file app;
   allow it for this install. (It is a debug build, so Play Protect may show a warning; tap "Install anyway".)
2. Open **Rang Mausam** once. Allow approximate location, or type a city and tap **Set**.
   Pick your script (हिंदी, ಕನ್ನಡ, தமிழ், বাংলা) and °C or °F.
3. Long-press the home screen, choose **Widgets**, find Rang Mausam, and drag it out. Resize it to switch
   between the small, medium and large layouts.

The widget refreshes about every 30 minutes (Android's minimum for widgets). Tap it to open the app;
**Refresh widget now** forces an update. If the phone kills background work aggressively (some Xiaomi, Oppo,
Vivo and Samsung battery modes), set Rang Mausam's battery use to "Unrestricted".

## What it shows

| Weather | Objects | Colour |
|---|---|---|
| Sunshine | Straw hat, sunglasses | Marigold |
| Scorching (35 °C+) | Clay matka, hand pankha | Sindoor red |
| Cloudy | Block-print kurta, jhola | Indigo blue |
| Rain, now or within 12 h (50%+) | Raincoat, chhata | Monsoon green |
| Thunderstorm | Kulhad chai, pakoras on a leaf | Night indigo |
| Snow | Paisley snow jacket, boots | Kashmiri blue on white |
| Fog | Monkey cap, muffler | Sage |
| Cold (8 °C or less) | Shawl, chai | Maroon |
| Windy (30 km/h+) | Patang, flying dupatta | Peacock teal |
| Clear night | Diyas under a crescent | Night blue |

Priority when several apply: storm, snow, rain, fog, scorching, windy, cold, then clear or cloudy.

## Code map

- `app/src/main/java/com/rangmausam/Ink.kt` : all drawing (objects, decor, frames, layouts).
- `Weather.kt` : Open-Meteo request, city search, and the rules that pick the weather state.
- `RangWidget.kt` : the widget, size detection, caching, location.
- `MainActivity.kt` : settings screen and a gallery of every state.

Credits: forecast data by Open-Meteo.com (CC BY 4.0). Fonts Playfair Display and Lora, SIL Open Font License
(licence texts in `app/src/main/assets/fonts`).
