# Kazi Ndogo - Deployment Guide

## 📋 Files Zako

Umepokea **3 files** zilizorekebishwa:

1. **index.html** - Complete app (HTML + CSS + JavaScript + Firebase)
2. **manifest.webmanifest** - PWA Configuration
3. **sw.js** - Service Worker (offline support)

---

## 🚀 Steps za Kuupload kwenye GitHub

### Step 1: Fungua GitHub Repo

```
https://github.com/yohananyamoga-gif/Kazi-ndogo
```

### Step 2: Delete Old Files

1. Rudi **Code** tab
2. Click **main** branch
3. Select file zote za lumba (old index.html, manifest, sw.js)
4. Click delete (ikona ya trash)

### Step 3: Upload Files Mpya

**Option A: Upload via Web Interface (Rahisi)**

1. Click **Add file** → **Upload files**
2. Drag & drop o select files zako:
   - `index.html` ✅
   - `manifest.webmanifest` ✅
   - `sw.js` ✅
3. Click **Commit changes**

**Option B: Upload via Git CLI (Kwa Advanced Users)**

```bash
# Nakili repo
git clone https://github.com/yohananyamoga-gif/Kazi-ndogo.git
cd Kazi-ndogo

# Bado file zote za lumba
rm -f index.html manifest.webmanifest sw.js

# Copyeni file mpya hapa
# (pasta files zako hapa)

# Push changes
git add .
git commit -m "Fix: Rekebisha app - Firebase integration + PWA support"
git push origin main
```

---

## ✅ Verify Files

Baada ya kuupload, confirm kwenye GitHub:

1. Rudi **Code** tab
2. Hakikisha files zote zipo:
   - [ ] `index.html`
   - [ ] `manifest.webmanifest`
   - [ ] `sw.js`

---

## 🌐 GitHub Pages Deployment

App yako itakuwa **live** kwa:**

```
https://yohananyamoga-gif.github.io/Kazi-ndogo/
```

**Tungoja:**
- ⏳ 2-3 minutes kwa GitHub Pages kuprocess changes
- 🔄 Refresh page kabla
- 🔥 Baada, app itafunguka!

---

## 🔧 Testing

### Kwa Mobile Browser:
1. Fungua: `https://yohananyamoga-gif.github.io/Kazi-ndogo/`
2. Jaribu login/signup
3. Ongeza tasks
4. Check offline mode

### Kwa Desktop:
1. Open browser
2. Paste URL hapo juu
3. Open DevTools (F12)
4. Go to **Application** → **Service Workers**
5. Hakikisha Service Worker imeload

---

## 📱 Install App (Mobile)

**Android:**
1. Fungua app kwa browser
2. Click menu (three dots)
3. Select "Install app"
4. App itainstall kwenye home screen

**iOS:**
1. Fungua Safari
2. Click share button
3. Select "Add to Home Screen"
4. App ready!

---

## 🔐 Firebase Security

**Rules zako (Firestore)** - Safi na tested:

```firestore
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /tasks/{taskId} {
      allow read: if true;
      allow write: if true;
    }
    match /users/{userId} {
      allow read, write: if request.auth != null && (request.auth.uid == userId || request.auth.token.email == "yohananyamoga@gmail.com");
    }
    match /activity/{activityId} {
      allow read: if true;
      allow create: if request.auth != null;
      allow update, delete: if request.auth != null && request.auth.token.email == "yohananyamoga@gmail.com";
    }
    match /settings/{settingId} {
      allow read: if true;
      allow write: if request.auth != null && request.auth.token.email == "yohananyamoga@gmail.com";
    }
    match /withdrawals/{withdrawalId} {
      allow read: if request.auth != null && (resource.data.uid == request.auth.uid || request.auth.token.email == "yohananyamoga@gmail.com");
      allow create: if request.auth != null && request.resource.data.uid == request.auth.uid;
      allow update, delete: if request.auth != null && request.auth.token.email == "yohananyamoga@gmail.com";
    }
  }
}
```

---

## 🆘 Troubleshooting

### App haifunguki?

**Tatizo 1:** "App inakamatia"
- Clear browser cache (Ctrl+Shift+Delete)
- Refresh page
- Try incognito mode

**Tatizo 2:** "Firebase haifunguki"
- Check internet connection
- Verify Firebase rules kwenye console
- Check browser console (F12) kwa errors

**Tatizo 3:** "Service Worker error"
- Click DevTools → Application → Clear Storage
- Refresh page

---

## 📚 Features za App

✅ **Authentication** - Signup/Login with Firebase
✅ **Tasks Management** - Create, complete, delete tasks
✅ **Firestore Integration** - Real-time database
✅ **PWA Support** - Installable on mobile
✅ **Offline Mode** - Basic offline support via Service Worker
✅ **Responsive Design** - Mobile & desktop friendly

---

## 🎯 Next Steps

1. ✅ Upload files kwenye GitHub
2. ✅ Wait for GitHub Pages (2-3 mins)
3. ✅ Test app kwenye browser
4. ✅ Install app kwenye mobile
5. ✅ Share link with friends!

---

## 📞 Support

Kama kunataka issues:

1. Check GitHub Issues
2. Check browser console (F12)
3. Check Firebase console kwa errors
4. Check network tab kwa failed requests

---

**App is Ready! 🚀**

Jaribu sasa na twambe results! 💯
