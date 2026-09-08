# Standalone Android APK (post-submission portfolio)

This [main-account portfolio copy](https://github.com/tachiiB/BanoQabil-x-AliBaba-Cloud-AI-Hackathon-HumAahang) is independent of the frozen hackathon repository and Railway deployment. Do not add a push remote pointing to the submitted repository, publish a release there, or redeploy its service.

## Build

Run in a clone of this main-account repository, not the original hackathon folder:

```powershell
npx eas-cli@23.2.0 login --browser
npx eas-cli@23.2.0 build --platform android --profile preview
```

An Expo account with permission to the configured `@tahajay/hum-ahang-android-portfolio` project is required. Other contributors should create/link their own Expo project rather than attempting to use the owner's credentials. The preview profile creates a signed APK with bundled JavaScript, not an Expo Go/development-client app. Use available free build quota; do not accept a paid plan or paid build without approval. Store signing credentials securely; never commit them or paste them into chat. Download the APK from the completed build page.

For an isolated copy whose Git metadata is intentionally not used, set `EAS_NO_VCS=1` and `EAS_PROJECT_ROOT` to that copy's absolute path for the build command. This disables CLI Git operations; it does not bypass source exclusions or authentication.

The existing local Android toolchain is incomplete (NDK absent) and disk headroom is low, so cloud compilation avoids installing a large native toolchain on this PC.

## Connectivity and privacy

The public Railway HTTPS URL is configured through EXPO_PUBLIC_STT_URL at build time. No provider key, operator token or private judge invitation belongs in the APK. AI features require internet and a valid runtime session through Profile → Settings → Speech setup. Existing operator pairing codes are short-lived and single-use, and the session is memory-only. The web judge link is not a native login mechanism.

Opening a feature does not grant microphone/camera permissions automatically. Permission denial must leave a usable retry/type path. Native device dictation and text-to-speech depend on installed OS services and voices.

## APK acceptance checks

1. Install on a compatible Android phone; open with Expo/Metro terminals stopped. Home and onboarding must load.
2. Select Urdu; inspect menus, RTL text, navigation buttons and optional gestures. Switch back to English.
3. Type in conversation, explicitly switch speaker A/B, and check FTF's opposing panels.
4. Allow microphone permission only when requested. Test ordinary device dictation and cloud captions separately. For cloud captions first pair using the existing authorized setup, then verify Urdu and English input/output, stop and microphone release.
5. Capture/review a non-personal object, explicitly Analyze, and test translated result and read-aloud. Do not treat pose recognition as full sign translation.
6. Deny camera/mic permission and disconnect internet: show actionable errors, no frozen recording or fake success.
7. Test Quick Speak and Stop with the installed Urdu voice. Opening Emergency must not call anyone; opening Passport must not share or reveal QR automatically.
8. Force-close/reopen: local preferences should remain, while cloud features may require re-pairing. No private session should be included in the installer.

Publish only after testing, as an APK asset on a release in the new main-account repository. Keep the source commit and actual checks in release notes; a JavaScript export alone is not an APK or a successful physical-device test.
