# InkMate ✍️

A student-to-student **handwriting marketplace** built with Next.js. Students find other students who write handwritten notes, assignments and project documentation — and writers create a profile, upload handwriting samples, set their rate and manage requests.

> **No payments, ever.** InkMate does not process, collect or guarantee money. The per-page rate is shown as information only, and payment + physical exchange are arranged directly between students. There is no wallet, no gateway, no commission and no earnings tracking.

## Features

- **Home** — greeting, Find a Writer / Become a Writer, recommended writers, safety notice
- **Search** — live search by name, college, course or style, with filters (college, availability, rating, rate, style), recent searches and infinite scroll
- **Writer profiles** — verified badge, rating, rate per page, completed count, about, writing details, availability schedule, handwriting sample grid, request / message / report / block
- **Requests** — received / sent tabs with statuses (pending, accepted, declined, in progress, completed, cancelled), accept / decline / start / complete / cancel actions, and post-completion reviews
- **Messages & chat** — realtime one-to-one chat with image attachments, date dividers and unread indicators (no payment buttons anywhere)
- **Profile** — writer-mode toggle, activity stats (requests only), edit profile, writer settings (samples, rate, availability), privacy & safety, blocked users, report history, notifications, change password, delete account
- **Auth** — sign up, sign in, password reset (Supabase Auth)

## Tech stack

- [Next.js 16](https://nextjs.org) (App Router, TypeScript, Tailwind CSS v4, Turbopack)
- [Supabase](https://supabase.com) — Auth, PostgreSQL, Storage, Realtime (optional)
- [lucide-react](https://lucide.dev) icons
- Dark, mobile-first UI with a fixed bottom navigation

## Two backends, one interface

| Mode | When | Data |
|---|---|---|
| **Demo** | No env vars set | localStorage + realistic seeded dataset (10 writers, conversations, requests) — instantly explorable |
| **Supabase** | `NEXT_PUBLIC_SUPABASE_URL` + `NEXT_PUBLIC_SUPABASE_ANON_KEY` set | Real accounts, Postgres, Storage uploads, realtime chat |

The app switches automatically. Demo mode also simulates chat replies from seeded writers so the product feels alive.

## Getting started

```bash
npm install
npm run dev
```

Open http://localhost:3000 — you'll be signed into the demo account automatically. Demo credentials: `demo@inkmate.app` / `demo1234`.

### Running checks

```bash
npm run lint
npx tsc --noEmit
npm run build
```

## Going live with Supabase

1. Create a Supabase project.
2. Run the SQL in `supabase/schema.sql` in the Supabase SQL editor (tables, RLS, storage buckets, and the `delete_my_account` RPC — **no payment tables**).
3. Create a `.env.local`:

   ```env
   NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
   ```

4. Deploy anywhere Node is supported (Vercel, Netlify, Railway…).

## Deployment

Works out of the box in demo mode on any platform. This project is ready to push to GitHub and connect to Vercel.

## Safety

- "Stay safe. Never share passwords, OTPs or sensitive personal information."
- "Payments and physical exchange are arranged directly between students. InkMate does not process or guarantee payments."
- Every writer profile has Report and Block; reports are stored for moderation.
