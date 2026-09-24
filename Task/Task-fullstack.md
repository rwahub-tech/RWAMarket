# RWAHub Full Stack Test

You will receive access to the existing RWAHub codebase for review.

**Do not make changes directly to our repository.**

Create your own GitHub repository, copy the required project code into it, and complete the task there.


---

## How to run

```bash
cp example.env .env
# Windows PowerShell: Copy-Item example.env .env

npm install
npm run dev
```

- App: http://localhost:5173
- API health: http://localhost:3001/api/health

Do not commit `.env`.

---

## Task

Review the existing RWAHub app and make **one meaningful full stack Auth improvement**.

The change must go through **both** layers:

* Backend in `src/server` (a real API change)
* Frontend that already calls that API (a real UI change)

Today, wallet Sign In is mostly local client state. `/api/auth` JWT and API identity are not the same thing. Swapping `optionalAuth` for `authenticateToken` on one route is **not enough**.

The required special part is **Auth**. Your change must do all of the following:

* Sign In (email or wallet) obtains a real JWT from `/api/auth`
* The UI stores that token and sends it on protected actions
* `POST /api/assets` rejects guests (`401`)
* Asset owner comes from `req.user` only, not from the request body
* The existing Sign In or Asset Creation UI shows success and `401` clearly

You should focus on **quality rather than quantity**.

Do not rebuild the entire application. Do not make this a frontend-only, backend-only, or Solidity-only task.

Verify the change in the **existing UI** only. Do not use curl or Postman.

### Security Review

As part of the task, identify **1–2** frontend or backend security issues or risks you notice in the existing code.

Create:

```text
SECURITY.md
```

For each issue, briefly explain:

* What you found
* Risk level
* Why it matters
* How you would fix it

You do not need to fix every security issue.

---

## Expected Submission

Create your own **GitHub repository** containing your completed work.

Please send:

### 1. GitHub Repository

A link to your repository with the completed implementation.

The repository should contain the actual source code, not just screenshots.

### 2. Loom Video

Record a **5–10 minute Loom video** showing:

* Your implementation
* Sign In obtaining a JWT from `/api/auth`
* Guest `POST /api/assets` failing with `401` in the existing UI
* Signed-in create-asset using `req.user` as owner
* Security issues you identified
* Brief explanation of your technical decisions

Please send the Loom link together with your GitHub repository.

### 3. Short Summary

Include a short message:

```text
GitHub:
[repository link]

Loom:
[video link]

Summary:
- How Sign In now gets a JWT from /api/auth
- How the UI sends that token
- How POST /api/assets uses req.user and rejects guests
- Which existing UI page shows success and 401
- Security issues identified
- What I would improve next
```

---

## Evaluation

We will review:

* Understanding of the existing React and Express code
* Whether the UI and API stay in sync
* Error handling on both sides
* Code structure
* Security awareness
* Ability to make a practical, focused change across layers

**Pass:** Sign In issues a JWT, the UI sends it, `POST /api/assets` requires it and sets owner from `req.user`, success and `401` are shown in the existing UI, plus `SECURITY.md` with 1–2 issues.


**We are not expecting a complete production application.**

The goal is to see how you take an existing full stack Web3 app, improve one slice through API and UI, and explain your decisions.
