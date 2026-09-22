# 🧪 OrangeHRM Selenium Automation

Automated end-to-end UI testing for the [OrangeHRM](https://opensource-demo.orangehrmlive.com) demo application using **Selenium WebDriver** and **Node.js**, built with the **Page Object Model (POM)** design pattern.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Architecture](#architecture)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This project provides a scalable and maintainable test automation framework for the OrangeHRM Human Resource Management web application. It automates critical user workflows — starting with login/authentication — using a clean, object-oriented architecture that separates page interactions from test logic.

### ✅ Currently Automated

| Module         | Scenario              | Status |
| -------------- | --------------------- | ------ |
| Authentication | Login with valid creds | ✅     |

---

## Tech Stack

| Technology                                                       | Purpose                       |
| ---------------------------------------------------------------- | ----------------------------- |
| [Node.js](https://nodejs.org/)                                   | JavaScript runtime            |
| [Selenium WebDriver](https://www.selenium.dev/) `4.49+`         | Browser automation engine     |
| [Google Chrome](https://www.google.com/chrome/)                  | Target browser                |
| ES Modules (`"type": "module"`)                                  | Modern JavaScript import/export |

---

## Project Structure

```
shopwithselenium/
├── page/                   # Page Object classes
│   ├── base.js             # BasePage — shared driver & browser helpers
│   └── SignUpPage.js       # Login page — locators & interaction methods
├── test/                   # Test scripts
│   └── SignUpTest.js       # Login flow test
├── package.json            # Project metadata & dependencies
├── .gitignore              # Ignored files (node_modules/)
└── README.md               # ← You are here
```

---

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** — v18 or higher ([download](https://nodejs.org/))
- **Google Chrome** — latest stable version
- **ChromeDriver** — compatible with your Chrome version  
  > 💡 Selenium 4.49+ includes automatic driver management via [Selenium Manager](https://www.selenium.dev/documentation/selenium_manager/), so manual ChromeDriver installation is typically not required.

---

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-username/orangehrm-selenium-automation.git
   cd orangehrm-selenium-automation
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

---

## Usage

### Run the login test

```bash
node test/SignUpTest.js
```

This will:

1. Launch a Chrome browser window
2. Navigate to the OrangeHRM demo login page
3. Enter the username (`Admin`) and password (`admin123`)
4. Click the **Login** button
5. Leave the browser open for visual verification

> **Note:** To automatically close the browser after the test, uncomment the last line in [`test/SignUpTest.js`](test/SignUpTest.js):
>
> ```js
> await pages.browserClose();
> ```

### Demo Credentials

| Field    | Value      |
| -------- | ---------- |
| Username | `Admin`    |
| Password | `admin123` |

These are the default credentials for the [OrangeHRM demo site](https://opensource-demo.orangehrmlive.com/web/index.php/auth/login).

---

## Architecture

This project follows the **Page Object Model (POM)** pattern to ensure clean separation of concerns:

```
┌─────────────────────────────────────────────┐
│                 Test Layer                  │
│           (test/SignUpTest.js)              │
│  Orchestrates user scenarios using page     │
│  objects — no raw Selenium calls here.      │
├─────────────────────────────────────────────┤
│               Page Layer                    │
│          (page/SignUpPage.js)               │
│  Encapsulates locators & interaction        │
│  methods for a specific page.               │
├─────────────────────────────────────────────┤
│               Base Layer                    │
│            (page/base.js)                   │
│  Initializes WebDriver, provides shared     │
│  utilities (open URL, close browser).       │
└─────────────────────────────────────────────┘
```

### Key Design Decisions

- **Explicit Waits** — Every element interaction uses `driver.wait()` with `until.elementLocated` and `until.elementIsVisible` for reliable, flake-resistant tests.
- **ES Modules** — The project uses native ES module syntax (`import`/`export`) instead of CommonJS `require`.
- **Inheritance** — `SignUpPage` extends `BasePage`, inheriting driver initialization and browser lifecycle methods.

---

## Contributing

Contributions are welcome! To add automation for a new page:

1. Create a new Page Object in `page/` extending `BasePage`
2. Define element locators in the constructor
3. Add interaction methods with explicit waits
4. Create a corresponding test file in `test/`

```bash
# Example: adding a Dashboard page
page/DashboardPage.js    # Page Object
test/DashboardTest.js    # Test script
```

---

## License

This project is licensed under the **ISC License**. See the [package.json](package.json) for details.

---

<p align="center">
  <sub>Built with ❤️ by <strong>Fuad</strong> — for learning and practicing Selenium test automation.</sub>
</p>

