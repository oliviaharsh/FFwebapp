Overview

FluxFilm is a fully automated, self-serve subscription web app that allows users to purchase, pay for, resume, renew, and recover OTT subscriptions instantly — without login, without WhatsApp dependency, and without manual admin intervention.

The app is designed to feel like a mobile app, runs as a Single-Page Application (SPA), and is completely Google Sheets + Apps Script driven.

Key Principles

❌ No user login or signup

❌ No WhatsApp dependency

❌ No waiting for admin

✅ Instant or guided manual fulfillment

✅ Sheet-driven logic (plans, pricing, coupons)

✅ Secure payment verification

✅ Resume payment if user closes the app

Tech Stack

Frontend

HTML + CSS + Vanilla JS

Mobile-first SPA with slide navigation

Hosted via Google Apps Script HTMLService

Backend

Google Apps Script

Google Sheets as database

Database (Sheets)

PLANS

ORDERS

SUBSCRIPTIONS

INVENTORY (Accounts / Profiles / Capacity)

COUPONS & COUPON_USAGE

BANK (UPI transactions)

EMAIL_LOGS / INVOICE_LOGS

Payments

UPI deep links + QR

Deterministic payment note (OrderID)

User Flow — How FluxFilm Works
1️⃣ Home Screen

User lands directly on the app (no login).

Options:

Buy New Subscription

Manage / Renew (existing users)

Recover Access

Resume Payment (if pending)

2️⃣ Buy Flow
Step 1: Choose Service

User selects a service (Netflix, Prime Video, YouTube, etc.).

Each service is dynamically loaded from the PLANS sheet.

Step 2: Choose Plan

User selects a plan:

Duration

Price

Fulfillment type (Instant / Manual)

Benefits & badge (e.g. Most Popular)

Plans are fully sheet-controlled.

Step 3: Group Join (if required)

For group plans:

User must join a WhatsApp group

App shows warning & join link

User confirms they’ve joined before continuing

Step 4: Enter Details

User provides:

Email (for confirmation & invoice)

Phone number (primary identity)

Optional coupon code

Optional notes / affiliate ID

Extra required fields (e.g. Prime device type, YouTube email)

Step 5: Apply Coupon (Optional)

Coupons are:

Phone-based

Validated before order creation

Discount preview shown instantly

Coupons are locked only after successful payment.

3️⃣ Review Order

User sees:

Service & plan

Email & phone

Base price

Discount (if any)

Final payable amount

User confirms → order is created.

4️⃣ Payment Step

Unique OrderID generated (e.g. FF-12345)

UPI link + QR shown

OrderID must be added as UPI payment note

Copy buttons for everything

User pays → clicks “I’ve Paid → Verify”

5️⃣ Payment Verification

Backend:

Scans bank sheet for matching CREDIT entry

Matches amount + OrderID (with or without hyphen)

Marks order as PAID

If not detected:

User can retry verification

No order is lost

6️⃣ Fulfillment
Instant Plans

Inventory allocated automatically

Credentials generated

Subscription record created

Access shown on screen

Email + invoice sent

Manual Plans

Task created for admin

Status marked MANUAL_PENDING

User shown confirmation message

Email sent

7️⃣ Important Info Screen

Some plans show a post-payment message (from PLANS sheet), e.g.:

Device rules

Group warnings

Usage instructions

User must acknowledge before seeing access.

8️⃣ Done Screen

User sees:

Login ID

Password

Profile details (Netflix)

Copy buttons

Confirmation message

Email + invoice are always sent.

Resume Payment (Critical Feature)

If user:

Closes browser

Loses internet

Forgets OrderID

They can:

Click Resume Payment

Enter phone number

App fetches last pending order

Rebuilds payment screen automatically

👉 Users never need to remember OrderID.

Manage / Renew Flow

User enters phone number:

Active subscriptions are shown

Expiry date & days left visible

Options:

Renew early (with discount)

Renew expired plan

Renewals follow the same payment & verification flow.

Recover Access

If user loses credentials:

Phone + email verification

Active subscriptions shown

Credentials displayed again

Email resent automatically

Coupon System

Coupons are:

Fully sheet-controlled

Flat or percentage

First-time only support

Per-user & global limits

Service / plan restrictions

Coupons are consumed only after payment success.

Admin Control Philosophy

No admin dashboard exposed to users

Admin controls everything via Sheets

Manual overrides supported

Telegram alerts (optional)

Fully auditable logs

Core Value Proposition

FluxFilm turns subscription buying into a self-serve, app-like experience —
fast, secure, automated, and frustration-free.
