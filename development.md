---
layout: default
title: Local Development Guide
---

# Rainbow Locator - Local Development Guide

Rainbow Locator is a centralized Lost and Found web application for the University of Hawaiʻi at Mānoa. This guide provides instructions for setting up the development environment on your local machine.

## Prerequisites

Ensure you have the following installed:
- [Node.js](https://nodejs.org/) (v20 or higher recommended)
- [PostgreSQL](https://www.postgresql.org/) (Running locally or accessible via network)

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/pacifcbytes/rainbow-locator.git
   cd rainbow-locator
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

## Environment Setup

1. **Create a `.env` file:**
   Copy the provided `sample.env` to a new file named `.env`.
   ```bash
   cp sample.env .env
   ```

2. **Configure your environment variables:**
   Open `.env` and update the following:
   - `DATABASE_URL`: Your PostgreSQL connection string.
   - `AUTH_SECRET`: A secure random string for NextAuth (you can generate one with `openssl rand -base64 32`).
   - `AUTH_URL`: Set to `http://localhost:3000` for local development.

## Database Setup (Prisma)

This project uses Prisma ORM. Follow these steps to initialize your database:

1. **Generate the Prisma Client:**
   ```bash
   npx prisma generate
   ```

2. **Push the schema to your database:**
   ```bash
   npx prisma db push
   ```

3. **Seed the database:**
   Run the seed script to populate the database with initial data:
   ```bash
   npm run seed
   ```

## Running the Application

Start the development server:
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Available Scripts

- `npm run dev`: Runs the app in development mode.
- `npm run build`: Builds the app for production.
- `npm run start`: Starts the production server.
- `npm run lint`: Runs ESLint to check for code quality issues.
- `npm run seed`: Seeds the database using `src/seed.ts`.
- `npm run playwright`: Runs end-to-end tests.

## Testing

We use Playwright for end-to-end testing.

1. **Install Playwright browsers:**
   ```bash
   npx playwright install
   ```

2. **Run tests:**
   ```bash
   npm run playwright
   ```
