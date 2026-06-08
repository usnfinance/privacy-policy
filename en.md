# Privacy Policy — USN Finance

**Effective date:** 06/08/2026  
**Last updated:** 06/08/2026

## 1. Who we are

Operator of the **USN Finance** mobile application (the “App”, “we”, “us”):

- **FOP Nynko Serhii Fedorovych** (sole proprietor, Ukraine)
- **Registered address:** 17d Chervonoi Kalyny St., apt. 60, Kyiv, 02225, Ukraine
- Email: **usnfinance@gmail.com**

The current version of this Policy is always available at: **https://usnfinance.github.io/privacy-policy/en.html**

## 2. Overview

This Policy explains what personal and account-related data we collect, how we use it, who we share it with, and what rights you have.

By using the App, you agree to this Policy. If you do not agree, please do not use the App.

The App is intended for adults (18+) for personal and family financial tracking. We do not knowingly collect data from children under 13.

## 3. Data we process

### 3.1. Account and profile

- **Email address** — for sign-in via magic link (one-time link sent by email);
- **Nickname** — set once at registration, one per account; displayed in accounting groups;
- **Interface language** — your preference settings.

### 3.2. Financial and accounting data

- transaction amounts, **account balances by currency**, dates, categories, accounting structure;
- group names;
- **encrypted on the device (AES-256-GCM) and stored on the server in encrypted form:** transaction notes, accounting object names, and all currency reference fields — **name**, **code**, and **symbol**;
- transaction amounts, **account balances** (amount and currency identifier), and dates are stored on the server in plain form; balances are updated based on entered transactions.

### 3.3. Cryptographic data

- public keys and encrypted private keys (for shared group access);
- on your device in secure storage: session tokens, master key, group keys.

The **secret phrase** you create when setting up a group is **not sent to our server**. It is used only on your device to derive encryption keys.

### 3.4. Receipt recognition (only when you request it)

At your request, the App may process:

- **receipt photos** (camera or gallery);
- **receipt text** (paste, web page URL, QR/barcode);
- **category names** for matching line items.

This data is sent to our server (Supabase Edge Function) and then to **OpenAI** for automated recognition. Processing happens **within a single request**; the result is returned to the App.

Receipt content (image or text) is **not stored in our database**. We do **not** keep a receipt recognition log. Processing by OpenAI is governed by [their privacy policy](https://openai.com/policies/privacy-policy).

When scan credits are charged (if that feature is enabled), we may store **operational data only** in the database: OpenAI token counts, charge amount, profile and group identifiers — **not** receipt content.

### 3.5. Shared groups

If you invite a member to a group, we process the invitee’s **email address** to find a registered account and send an invitation.

### 3.6. Roles, access, and shared data

The App uses **accounting groups** — shared spaces where multiple users can maintain one set of financial records.

#### Access levels

**Account** — tied to your email. On first registration we create **one user profile**; your **nickname** is set once at registration and shown in every group you join. One email may belong to multiple accounting groups under the same profile.

**Group owner** — the user who created the group. The owner may:

- send invitations to other users by email;
- rename or delete the group;
- remove pending or declined invitations (members with **Pending** or **Declined** status);
- revoke access for active members;
- reactivate access for members with **Access revoked** status;
- see the member list and nicknames.

**Group member** — an invited user. They may accept or decline an invitation (**Pending** status). After accepting, they gain access to that group’s data like other active members (subject to encryption key availability, see below).

There is no separate “admin” role — only **owner** and **member**.

#### Member statuses

- **Pending** — invitation sent, not yet accepted;
- **Active** — full group access;
- **Declined** — invitation rejected;
- **Access revoked** — owner revoked access;
- **Deleted** — the user deleted their account. They may appear in the group member list with this status and a retained nickname; they have no access to group data. Past entries they created may remain in the ledger with authorship shown.

Only **active** members use group data in the normal way. Members with **Deleted** status remain visible in the list for transparency of entry authorship but cannot access the group. Access to a specific group’s data is provided in the context of your **current session** (the group selected in the App).

#### What other members can see

If you belong to a group, other members of that group with access to its data or member list can see **nicknames of all group members** (including invited, access-revoked, and deleted accounts) and membership status.

**Active** members can additionally see:

- financial transactions, amounts, **account balances by currency**, dates, and accounting structure;
- who created or edited entries (profile identifier and nickname).

Other members’ emails are **not shown** in the group UI. Email is processed only when **inviting** someone — when the owner enters an address to find a registered user.

After a member deletes their account, their **nickname** may remain visible to other group members (in the list with **Deleted** status and when viewing entry authorship). Their email is no longer available.

#### Encryption key and read-only mode

Editing sensitive fields (notes, object names, currency fields, etc.) requires the **group encryption key** on your device, obtained via your **secret phrase** or recovered from secure device storage.

If the key is unavailable (for example, you signed in on a new device without entering your secret phrase), encrypted fields are shown **undecrypted** (as stored on the server), including **account and category names** in the object tree, **transaction notes**, and **currency reference fields** (name, code, symbol). Amounts, dates, and operation types (by category code) remain readable; in the transaction feed, the currency symbol may show as “#” without the key.

You **cannot** add, edit, or delete transactions until the key is restored (by entering your secret phrase or recovering from secure device storage, if available).

When inviting a member, the owner shares an encrypted group key tied to the invitee’s public key.

#### Deletion and retention within groups

- **Account deletion** removes groups you own. In **other users’** groups, your entries may remain; your **nickname is retained** and shown with **Deleted** status. Your email and encryption keys are removed or anonymized.
- **Group deletion** by the owner removes all group data for all members.
- **Access revocation** for an active member ends their access; their past entries may remain in the shared ledger.
- **Removing an invitation** (**Pending** or **Declined** status) deletes the membership record before the user joins the group.

### 3.7. In-app purchases

When you purchase a subscription or scan tokens for receipt recognition:

- payment is processed through **Google Play**;
- we receive subscription/purchase status via **RevenueCat** (user identifier, product, validity period, token balance).

Payment card data is processed by Google, not by us.

### 3.8. Exchange rates

Exchange rates are stored per accounting group and used to **convert amounts in reports** into a currency you choose (using the rate on the transaction date). Transactions and account balances remain recorded in their original currencies.

To import reference rates, the App calls the public **Frankfurter** API (`api.frankfurter.dev`) with currency codes and dates. No personal data is sent in these requests. You may also enter and edit rates manually.

### 3.9. Data export

At your request, the App builds a JSON file with group data and offers to save it via the system share sheet. Where the file is saved is up to you.

The export’s `users` block includes only **profile identifier** (`user_id`) and **nickname** (`nikname`). Email is **not** included in the export.

### 3.10. Technical data

- network requests to our backend (Supabase);
- session tokens to keep you signed in;
- profile and group identifiers on the server.

We do **not** use third-party advertising or analytics SDKs (Firebase Analytics, Crashlytics, etc.) to track your behavior.

## 4. Why we process data

- registration, sign-in, and session management;
- storing and syncing your financial records;
- encrypting sensitive text fields on the device;
- collaboration in accounting groups and member access management;
- receipt recognition at your request;
- building reports with conversion of amounts into a selected currency (exchange rates);
- paid features (subscription, scan tokens);
- data export;
- user support and legal compliance.

**Legal bases (GDPR):** contract performance (providing the service); consent (camera, gallery, receipt recognition); legitimate interest (account security).

## 5. Who we share data with

| Recipient | Purpose | Policy |
|-----------|---------|--------|
| **Supabase** | database hosting, authentication, server functions | [supabase.com/privacy](https://supabase.com/privacy) |
| **OpenAI** | receipt recognition (your action) | [openai.com/policies/privacy-policy](https://openai.com/policies/privacy-policy) |
| **Google Play** | payments and subscriptions | [policies.google.com/privacy](https://policies.google.com/privacy) |
| **RevenueCat** | subscription management | [revenuecat.com/privacy](https://www.revenuecat.com/privacy) |
| **Frankfurter** | reference exchange rates | [frankfurter.dev](https://www.frankfurter.dev/) |

We do **not sell** your personal data to third parties.

## 6. Where data is stored

Server data is hosted on **Supabase** (region: **Central Europe — Zurich, Switzerland**, `eu-central-2`).

Encryption keys and session data are stored locally on your device in the OS secure storage (Android Keystore / iOS Keychain).

## 7. Security

- encryption of sensitive fields on the device (AES-256-GCM) before storage on the server;
- asymmetric encryption (X25519) for group key exchange — also on the device;
- secure local storage for keys;
- group data access limited to group members (server access policies);
- data in transit over HTTPS.

No system is 100% secure, but we apply reasonable technical and organizational safeguards.

## 8. Retention

Data is kept while your account is active.

After **account deletion** (via “Delete account” in the App):

- your data and groups you own are permanently deleted;
- your entries in other users’ groups may remain;
- your **nickname** may remain visible in others’ groups with **Deleted** status and in metadata of your entries;
- your account and email are deleted; cryptographic profile data is removed or anonymized;
- paid subscription is cancelled on our side; to stop future charges, cancel the subscription manually in Google Play.

When **access is revoked** for an active member, they lose access to group data; their past entries may remain in the shared ledger.

## 9. Your rights

You may:

- view and edit your profile in the App;
- export group data (JSON);
- **delete your account** in the App;
- revoke camera/gallery permission in device settings;
- cancel your subscription in Google Play.

For access, correction, deletion, or restriction requests, contact: **[usnfinance@gmail.com]**.

Residents of the EU and other jurisdictions with applicable law may lodge a complaint with their supervisory authority.

## 10. Device permissions

| Permission | Purpose |
|------------|---------|
| **Internet** | sync, authentication, services |
| **Camera** | receipt photos, QR/barcode scan for receipt URL |
| **Gallery / photos** | pick a receipt image (only when you choose to) |

Permissions are requested when you use the related feature.

## 11. Links and web content

For receipts by URL, the App may open a web page (WebView) or fetch its text. You enter or scan the link yourself. We do not control third-party website content.

## 12. Changes to this Policy

We may update this Policy. The last updated date is at the top. We will notify you of material changes in the App or by email where required by law.

## 13. Contact

**FOP Nynko Serhii Fedorovych**  
Registered address: 17d Chervonoi Kalyny St., apt. 60, Kyiv, 02225, Ukraine  
Email: **usnfinance@gmail.com**
