# AI Face Recognition & Attendance (Fully Offline Capable)

A complete **zero-server** face recognition attendance system with adaptive liveness detection.  
All AI models and the face-api library are included locally — no external CDN dependency for the AI part.

## Features

- Real-time face detection & recognition
- Adaptive liveness challenges (Blink / Smile / Head Turn Left / Right)
- Register multiple users (Name + ID)
- Mark attendance with liveness verification
- Attendance history + Export to CSV
- Data stored in browser `localStorage`
- Works completely offline after the page is loaded once

## Folder Structure

```
.
├── index.html              ← Main application
├── face-api.js             ← Local face-api library (~1.3 MB)
├── models/                 ← AI model files
│   ├── tiny_face_detector_model-weights_manifest.json
│   ├── tiny_face_detector_model.bin
│   ├── face_landmark_68_model-weights_manifest.json
│   ├── face_landmark_68_model.bin
│   ├── face_recognition_model-weights_manifest.json
│   └── face_recognition_model.bin
└── README.md
```

## How to Test Locally (Offline)

### Recommended way (local server)

Open terminal in this folder and run:

```bash
# Python 3
python -m http.server 8000

# or Node.js
npx serve .

# or PHP
php -S localhost:8000
```

Then open: **http://localhost:8000**

> Important: Camera access requires `http://localhost` or HTTPS.  
> Opening the HTML file directly (`file://`) may block the camera in some browsers.

### What happens on first load?
- The page loads the local `face-api.js` and model files from the `models/` folder.
- After that, everything works even if you disconnect from the internet.

## Deploy to GitHub Pages (Free Forever)

1. Create a **public** GitHub repository.
2. Upload **all files and the `models` folder**.
3. Go to **Settings → Pages**.
4. Source → Deploy from branch `main` → `/ (root)`.
5. Save.

Your site will be live at:  
`https://yourusername.github.io/repository-name/`

No external AI model dependency remains — everything is hosted on your GitHub repo.

## Notes

- Tailwind CSS is still loaded from CDN (only for styling). The AI part is fully self-contained.
- Data (registered faces + attendance) is stored only in the browser’s localStorage.
- Best experience on Chrome / Edge / Firefox (desktop).
- Total size of models ≈ 6.8 MB (mostly the face recognition model).

---

Fully offline-capable • Zero-server • Privacy friendly
