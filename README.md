# Supabase Auth Vault

A React Native application built with Expo and Supabase Auth. It includes a
SecureStore-backed session vault, an authentication route guard, and a tactical
mission board with Supabase CRUD operations protected by Row Level Security
(RLS) policies configured in your Supabase project.

## Requirements

- Node.js and npm
- A Supabase project with Authentication enabled
- A `missions` table with RLS enabled and policies that limit access to each
  authenticated user's own rows

## Setup

1. Install the project dependencies:

   ```sh
   npm install
   ```

2. Create a local environment file from the template:

   ```sh
   cp .env.example .env
   ```

3. Set `EXPO_PUBLIC_SUPABASE_URL` and `EXPO_PUBLIC_SUPABASE_ANON_KEY` in `.env`
   to your Supabase project's URL and anon/public key.

4. Start Expo:

   ```sh
   npm run start
   ```

   Use the Expo CLI prompts to open the app on a device, emulator, or web
   browser. You can also run `npm run android`, `npm run ios`, or `npm run web`.

## Features

- **Supabase Auth:** email/password registration and sign-in.
- **SecureStore Vault:** persists the Supabase session using Expo SecureStore on
  native platforms.
- **Route Guard:** redirects signed-out users to login and authenticated users
  away from the login screen.
- **Tactical Mission Board:** create, list, update, and delete missions through
  Supabase; configure RLS policies in Supabase to enforce per-user access.

## Credential safety

Keep `.env` local; it is excluded by `.gitignore`. Never commit real environment
values or a Supabase `service_role` key. Expo `EXPO_PUBLIC_` variables are
available in the client app, so use only the anon/public key and rely on RLS
policies to protect database data. `.env.example` contains variable names only.
