# Mobile Developer Assessment: Virtual Video Chat Simulator (Mid/Senior Level)

## Overview
Build a clean, well-architected Android app in Kotlin that simulates a video conversation with a virtual anime-style character. The app plays pre-recorded video responses based on simple keyword detection from the user's speech.

This task is designed to evaluate your ability to:
- Handle seamless video playback and state transitions
- Integrate Android SpeechRecognizer with proper lifecycle awareness
- Write maintainable, production-quality code
- Think about UX polish and edge cases

We estimate this should take **15–25 hours** for an experienced developer (roughly 2–4 focused days). Please do **not** spend more than 25 hours — quality and clean architecture matter far more than completing every stretch goal.

## Core Requirements (Must-Have for Strong Consideration)

### 1. Video Playback & State Machine
Implement smooth transitions between these states with **no visible gaps, black screens, or buffering**:

- **Idle** → Looping standby video (virtual person waiting patiently)
- **Greeting** → Plays on "Start Chat" tap
- **Listening** → Looping attentive video + microphone active
- **Response** → Plays appropriate pre-recorded video based on detected keywords
- **Back to Listening** → After response ends
- **Goodbye** → Ends conversation and returns to Idle

**Critical**: Use preloading or prepare-next-video technique so transitions feel instant.

### 2. Speech Recognition Basics
- Use Android's `SpeechRecognizer` API
- Request microphone permission gracefully
- Start listening automatically when Listening video begins
- Stop listening once speech result is received
- Trigger responses based on these keywords (case-insensitive, partial matches OK):
  - "hello", "hi" → greeting-like response (or reuse general)
  - "weather", "today" → weather response
  - Anything else → general response ("I'm glad to hear that! ...")
- Handle basic failures → play fallback video ("I didn't catch that...")

### 3. Minimal Conversation Flow
1. App opens → Idle video loops + "Start Chat" button visible
2. Tap "Start Chat" → Greeting video
3. Greeting ends → Listening video + mic on
4. User speaks → Matching response video plays
5. Response ends → Listening video + mic on again
6. User says "goodbye" or similar → Goodbye video → back to Idle

## Stretch Goals (Nice-to-Have – Do These if Time Allows)
- Silence detection: After 8–10 seconds of no speech → play "Are you still there?" video, then resume Listening
- After second silence → auto-end with Goodbye
- Visual feedback while listening (e.g. subtle mic pulse or waveform)
- 2–3 unit tests (e.g. keyword matcher, state transitions)
- Handle app background/foreground gracefully (pause/resume videos & listening)

## Technical Requirements
- **Kotlin only**, Android (min SDK 29 / Android 10)
- **Video player**: ExoPlayer strongly recommended (MediaPlayer acceptable)
- **Architecture**: MVVM, MVI, or clean state machine pattern preferred
- **Provided assets**: We'll share a GitHub repo or zip with 6–8 MP4 videos (~5–10s each, 720p, 16:9)
  - idle.mp4, greeting.mp4, listening.mp4, weather.mp4, general_response.mp4, goodbye.mp4, fallback.mp4, prompt.mp4 (stretch)

You may enhance the UI/animations or add small creative touches if you want — but focus on core polish first.

## Deliverables
1. **Public GitHub repo** containing:
   - Full Android project (builds cleanly via Gradle)
   - README.md with:
     - Setup & run instructions
     - Architecture overview (why you chose it)
     - Video playback strategy (how you achieved seamlessness)
     - Speech integration & keyword approach
     - What is implemented vs. stretch goals
     - Challenges faced & solutions
     - Known limitations & future improvements
2. **(Highly recommended) 1–2 min screen recording** demoing:
   - Full flow (start → conversation → goodbye)
   - One failure case (e.g. "I didn't catch that")
   - Bonus: silence prompt if you implemented it

## Evaluation Criteria (Mid/Senior Focus)
- **Seamless video playback & state management** (35%) – This is the heart of the task
- **Clean, maintainable code & architecture** (30%)
- **SpeechRecognizer integration & error handling** (20%)
- **UX polish & thoughtful edge cases** (10%)
- **Clear documentation & communication** (5%)

## Note on AI Usage and Ownership Expectations
You may absolutely use AI to help with this task, even to one-shot major parts. What matters most is that you can explain the implementation thoroughly. At Masterbek, we must own the codebase and be responsible for it. That means for professional client work you need to understand, debug, extend, and refine every part of the source code you submit.

Some candidates will one-shot solutions with AI, but we prioritize understanding and the ability to polish the result to our transition requirements, especially the explicit requirement of no black screen and no buffering. By "black screen" we mean even a split-second black frame caused by switching between video players (often called a "black flash"). AI-generated solutions often miss this requirement, and it is a common deciding factor in selection.

We will review **partial submissions seriously** if the completed parts are high-quality. A beautifully implemented core flow + great README beats a buggy everything-attempted project.

## Time & Submission
- **Recommended effort**: 15–25 hours max
- **Deadline**: 7 calendar days from receipt of this task
- **Submit**: Send GitHub repo URL + optional demo link via Telegram to @masterbekuz
- **Extensions**: Available on request if you're making good progress

**Please submit even if incomplete** — we value seeing your process, priorities, and code quality more than 100% completion.

## Questions?
Reply to the task email within 48 hours — we'll respond quickly.

Good luck — we're excited to see what you build!