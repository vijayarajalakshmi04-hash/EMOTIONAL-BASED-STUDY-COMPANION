# StudyMind — Emotion-Based Study Companion

StudyMind is an AI-powered, emotion-aware study companion built as a single-page web application. It detects a user's emotional state—such as happy, stressed, tired, sad, or neutral—and adapts their study plan accordingly, offering smart suggestions, tracking productivity, and providing an interactive AI chatbot for motivation and study help.

## Features

- **Real-Time Emotion Detection**: Analyzes facial expressions using webcam input to detect the user's emotional state. (Currently uses a simulated Face API demo implementation).
- **AI Study Companion Chatbot**: Powered by Anthropic's Claude API, the chatbot serves as a personalized study mentor, interpreting emotional context to provide tailored advice and answers to study questions.
- **Voice Input & Output (TTS)**: Leverages the Web Speech API to allow users to interact with the chatbot using voice commands, with the AI reading responses aloud.
- **Mood & Productivity Dashboard**: Includes weekly study hour tracking, emotion distribution charts (built with Chart.js), and personalized study suggestions based on current mood and recent performance.
- **Responsive & Accessible Design**: A modern, mobile-friendly interface featuring Light and Dark modes, fluid transitions, glassmorphism UI elements, and highly readable typography.
- **Single Page Application (SPA)**: Custom-built vanilla routing for fast transitions between the Home, Features, Dashboard, Authentication, and Contact pages.

## Tech Stack

- **HTML5**: Semantic document structure.
- **CSS3**: Vanilla CSS with custom properties (variables) for theming and dark/light modes, animations, and fluid responsive design layouts (Flexbox and Grid).
- **JavaScript (ES6+)**: Vanilla JS for logic, form handling, DOM manipulation, navigation, webcam streaming, and asynchronous API calls.
- **External Libraries & APIs**:
  - [Chart.js](https://www.chartjs.org/) for rendering the Dashboard analytics natively on the canvas.
  - [Face-api.js](https://github.com/justadudewhohacks/face-api.js) structure setup for real-time facial expression tracking.
  - Anthropic's [Claude API](https://www.anthropic.com/api) integration for intelligent and context-aware chatbot messaging.
  - [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API) for voice transcription and synthesized speech playback.
- **Google Fonts**: Uses 'Syne' (Display) and 'DM Sans' (Body) for typography.

## Setup & Running Locally

Because StudyMind uses vanilla web technologies and does not depend on a build system like Webpack or Vite, it can be run directly in the browser. 

1. **Clone or Download the Repository**.
2. **Open the App**: Simply open `index (1).html` in any modern web browser.
3. **Important Note for Webcam APIs & External Fetching**: 
   Since the app accesses the user's webcam and makes cross-origin `fetch` requests to external APIs (like Anthropic), it is typically best to serve it over a local development server rather than the `file://` protocol. 
   - Using Python: Run `python -m http.server 8000` in the directory, then navigate to `http://localhost:8000/index (1).html`
   - Using Node/npm: Run `npx serve .` and navigate to the resulting local host link.

## API Setup (Claude)

Currently, the Application tries to run a client-side `fetch()` call directly to the Anthropic API:
```javascript
const resp = await fetch('https://api.anthropic.com/v1/messages', { ... })
```
> **Warning**: Making raw API calls directly from a frontend application will often be blocked by CORS unless you run a proxy, and it safely exposes API keys. For production use or further development, it is highly recommended to migrate these calls to a backend server (e.g., using Node.js/Express, Python/FastAPI, etc.) which securely holds your Anthropic API credentials.

## Project Structure

- `index (1).html`: The entirety of the web application. Contains the HTML structure, inlined CSS styles, and inlined JavaScript logic.

## Future Enhancements
- Properly load Face-api.js models and weights to replace the simulated behavior with actual real-time tensor operations.
- Introduce a Backend Server (Node.js/Python) to handle API key security and data persistence.
- Implement a Real Database (PostgreSQL/MongoDB) rather than losing user history on page reload.
