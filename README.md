# CyberGuard FL — VS Code project

A frontend-only React + TypeScript research dashboard for **Privacy-Preserving Federated Learning for Cyber Attack Detection in Banking Networks**.

## Run on Windows (beginner steps)
1. Extract this ZIP. Open the extracted `CyberGuard-FL` folder in Visual Studio Code using **File → Open Folder**.
2. In VS Code choose **Terminal → New Terminal**.
3. In PowerShell run `npm.cmd install`. (If using Command Prompt, use `npm install`.)
4. Start the app with `npm.cmd run dev` (or `npm run dev` in Command Prompt).
5. Open the local URL printed in the terminal, usually `http://localhost:5173`.
6. Keep the terminal open while using the site. Press `Ctrl+C` to stop it.

## Build
`npm.cmd run build`

## Pages
Overview · Dataset Explorer · Client Network · Federated Learning · Differential Privacy · Model Comparison · Attack Detection · Reports · About Project.

## Experiment facts represented
- CIC-IDS2017 public benchmark; 5 labels: BENIGN, DoS, DDoS, PortScan, Bot.
- 68 numeric features; 4 simulated non-IID clients; Dirichlet alpha 0.5; 5 rounds.
- Centralized: accuracy 98.78%, weighted precision 98.91%, recall 98.78%, F1 98.81%.
- FedAvg: accuracy 95.61%, weighted F1 95.58%.
- DP-FL: accuracy 92.36%, weighted F1 91.39%.
- Opacus DP-SGD: noise multiplier 1.0, max_grad_norm 1.0, delta 1e-5, final epsilon 5.4442.

## Important accuracy and research caveats
This is a **frontend prototype** only. No FastAPI backend or trained model inference is connected. Attack Detection runs a browser-side illustrative rule and must not be presented as live ML inference. Traffic class chart and per-client class percentages are explicitly illustrative, not verified dataset/client counts. CIC-IDS2017 is not real banking data; clients are simulated. The privacy experiment is example-level DP-SGD/accounting, not client-level DP. Secure RNG was disabled in the recorded Opacus experiment. No secure aggregation, production encryption, poisoning defence, or production banking deployment is implemented. Centralized training used class-weighted loss while FedAvg and DP-FL used ordinary CrossEntropyLoss, so comparison is informative rather than perfectly controlled.

## Backend integration later
The UI and experiment constants are separated in `src/data.ts`. Phase 2 can add FastAPI endpoints and replace demo interactions with real model predictions and artifact-backed metrics. Keep large datasets, model weights and credentials out of the frontend and public GitHub repository.
