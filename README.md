# How to Deploy Backend to Vercel (Node/ExpressJS)

---

### Step 1: Project Structure
- Keep your backend files structured. Ensure:
  - `app.ts` and `server.ts` are inside the `src` folder.
  - No deep or unnecessary subfolder nesting.

---

### Step 2: Lint Check
- Run: `npm run lint`
- Fix all **errors**.
- Fix **warnings** if possible (optional but better).
- Auto fix: `npm run lint:fix`
- Manual fix if needed.

---

### Step 3: Build
- Run: `npm run build`
- Solve any errors during build process.

---

### Step 4: Deploy to Vercel

#### 4.1: Create `vercel.json`
```json
{
  "version": 2,
  "builds": [
    {
      "src": "dist/server.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "(.*)",
      "dest": "dist/server.js"
    }
  ]
}
```
- Ensure `server.js` is located in the `dist` folder.

#### 4.2: Check in Vercel CLI
- Run: `vercel --prod`
- Setup options:
  - scope → select
  - link to existing project? → no
  - project name → type name
  - directory → `.` (current folder)

#### 4.3: Test GET API
- Use incognito mode or Postman to test.
- Check domain link from Vercel dashboard.

#### 4.4: CLI Commands
- Install Vercel CLI: `npm i -g vercel`
- Login: `vercel login`
- Deploy: `vercel --prod`

---

### Extra Scripts (optional)
Add to `package.json`:
```json
"scripts": {
  "start": "node ./dist/server.js",
  "start:prod": "nodemon ./dist/server.js"
}
```

---

### Useful Commands
- Uninstall Vercel: `npm uninstall -g vercel`
- Logout: `npx vercel logout`

---

### Notes:
- `npx` is a node package executor.
- `vercel` handles the build and deploy automatically.
- Make sure the `dist` folder contains the final build.

---

