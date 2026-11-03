# Nova-App-Downloads
Official NŌVA Android app downloads and release notes.

<div align="center">

# NÅŒVA â€” Clothing Store App

**Modern fashion. Simple shopping.**

A modern, mobile-first shopping app for **NÅŒVA**, a Sri Lankan unisex clothing brand.

Built with **React Native**, **Expo**, **TypeScript**, and **Firebase**.

</div>

---

## About

NÅŒVA is a fashion shopping experience designed around a clean, minimal interface, blue-tinted glass-inspired details, and smooth navigation. Customers can discover collections, view product details, manage their cart, and place orders from their phone.

> **Development note:** This README describes the project's intended features and setup. Some features may still be in progress; verify implementation against the current source code before marking the app production-ready.

## Highlights

- **Premium UI:** Minimal, glass-inspired design with light, dark, and subtle blue accents.
- **Account access:** Email/password and Google sign-in via Firebase Authentication.
- **Product discovery:** Home feed, collections, product details, images, prices in LKR, and offers.
- **Shopping cart:** Add and remove products and review the order before checkout.
- **Checkout:** Customer and delivery details with **Cash on Delivery** and **Bank Transfer** options.
- **Order tracking:** Follow an order using its order reference or tracking code.
- **Customer profile:** Update account details and profile photo.
- **Admin tools:** Manage products, collections, pricing, offers, and order statuses with role-based authorization.
- **In-app updates:** Check whether a newer release is available and direct users to a verified download source.
- **Android distribution:** Share installable Android builds through the NÅŒVA website or other supported distribution channels.

## Tech Stack

| Area | Technology |
| --- | --- |
| Mobile app | React Native + Expo |
| Language | TypeScript |
| Navigation | Expo Router |
| Authentication | Firebase Authentication |
| Database | Cloud Firestore |
| Image uploads | Cloudinary and/or Firebase Storage (depending on current configuration) |
| Motion | React Native Reanimated |
| Android builds | Expo Application Services (EAS Build) |

## Getting Started

### Requirements

- Node.js (current supported LTS release)
- npm
- Expo and EAS accounts (EAS required only for cloud builds)
- Firebase project with the required services enabled
- Android device or emulator for testing

### 1. Clone the project

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_NOVA_APP_REPOSITORY.git
cd YOUR_NOVA_APP_REPOSITORY
```

Replace the placeholder URL and folder name with the actual app repository.

### 2. Install dependencies

```bash
npm install
```

### 3. Configure the environment

Create a `.env` file at the project root and configure the Firebase public client settings used by the app:

```dotenv
EXPO_PUBLIC_FIREBASE_API_KEY=your_firebase_api_key
EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
EXPO_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
EXPO_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.firebasestorage.app
EXPO_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
EXPO_PUBLIC_FIREBASE_APP_ID=your_app_id
```

If the app uses additional variables (for example, a Cloudinary cloud name or upload preset), add **only the public client-side values** required by the code. Never expose Cloudinary API secrets, Firebase Admin SDK keys, signing credentials, or other server-side secrets in the app or repository.

> Firebase client configuration alone does **not** secure user data. Configure Firebase Authentication, Firestore Security Rules, and Storage Security Rules appropriately. Admin permissions must be enforced server-side or in security rules, not only by hiding admin UI.

### 4. Run the app

```bash
npx expo start
```

Open the project on a supported Android device or emulator. Features that require custom native modules may need an Expo development build rather than Expo Go.

## Android APK Builds

Configure `app.json` / `app.config.ts` and `eas.json` for your application before building. Then:

```bash
npx eas-cli login
npx eas-cli build --platform android --profile preview
```

The `preview` profile must be set up to produce an **APK** (for example, with `android.buildType: "apk"` in `eas.json`). Other profiles may produce an AAB instead.

### Updating an existing installation

For a new APK to install over an existing app, keep the **same Android package name and signing key**, and increment the Android `versionCode`. Changing the signing key or package name prevents a normal in-place update.

## Suggested App Sections

| Section | Purpose |
| --- | --- |
| Onboarding | Welcome screens, privacy notice, and consent where required |
| Authentication | Sign in / sign up / password recovery |
| Home | Featured items, new arrivals, promotions |
| Collections | Browse clothing by collection |
| Product | Photos, details, price, and availability |
| Cart & Checkout | Review purchases and enter delivery/payment details |
| Orders | View order history and track order progress |
| Profile | Personal details, profile image, and preferences |
| Admin | Authorized product, collection, offer, and order management |

## Security & Privacy

- Collect only the customer information needed for accounts, orders, and deliveries.
- Never store passwords directly in Firestore; use Firebase Authentication.
- Require authentication and ownership checks for private orders and profiles.
- Restrict product and order administration to authorized admins using security rules or trusted backend logic.
- Keep API secrets and service-account credentials outside client builds and public source control.
- Publish a privacy policy explaining data collection, storage, image uploads, and account deletion.

## Project Status

**Under active development.** Features, screen layouts, and service integrations may change as bugs are fixed and releases are prepared.

## Roadmap

- [ ] Complete end-to-end testing of product image uploads and management
- [ ] Validate collection browsing and product details
- [ ] Test profile saving and profile photo updates
- [ ] Verify checkout, order creation, and tracking flows
- [ ] Review admin authorization and Firestore rules
- [ ] Finalize in-app update checks and signed APK upgrades
- [ ] Complete accessibility, performance, and release QA

The checkboxes are a **verification checklist**, not a statement that all items are unimplemented.

## Contributing

Suggestions and bug reports are welcome through this repository's Issues section once it is enabled. Please do not post personal information, private Firebase configuration, or API secrets in issues.

## License

**All rights reserved**, unless a separate `LICENSE` file is added to this repository.

---

<div align="center">

Made for **NÅŒVA** â€” Sri Lanka ðŸ‡±ðŸ‡°

</div>