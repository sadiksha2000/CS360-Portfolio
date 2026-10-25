# CS360-Portfolio

**Sadiksha Pathak | CS-360 Mobile Architecture and Programming**

This repository holds my final project for CS-360: **Weight Tracker**, an Android app written in Java. The full project is in `SadikshaPathak_Option3_WeightTracker_ProjectThree.zip`. Unzip it and open the folder in Android Studio to run it.

## 1. App requirements and user needs

The app is for people who want to track their weight and reach a goal weight. Based on the project requirements, users needed to:

- Log in with their own private username and password, or create a new login
- Enter their daily weight and see their past weights in a simple grid
- Edit or delete an entry when they make a mistake
- Set a goal weight
- Get a text message when they reach their goal, but only if they choose to allow it

The app had to keep each person's data separate and keep working even if the user said no to text messages.

## 2. Screens and features, and how the UI supports the user

The app has three screens:

- **Login screen:** returning users log in and new users create an account. Error messages show under the field that needs fixing, and the login error does not say which part was wrong.
- **Weight History screen:** a summary card (goal, latest weight, amount to go), a grid of daily weights with Edit and Delete buttons, a form to add a weight, and a place to set the goal.
- **SMS Notifications screen:** the user can allow text permission, save a phone number, and send a test message.

For a user-centered design, I kept the screens simple with one main job each. I used large touch targets, clear labels, and a teal and amber color scheme that is easy to read. Every screen uses the same fade transition so the app feels consistent. An empty-grid message tells new users what to do first.

## 3. Coding approach

I used these techniques while building the app:

- **Separate classes for separate jobs.** `DatabaseHelper` handles all data, `SmsNotifier` handles texting, and each screen has its own Activity. Because of this, the SMS permission check lives in one place and is easy to find.
- **SQLite database with three tables** (users, weights, goals) linked with foreign keys, so deleting a user also deletes their data.
- **Secure passwords.** Passwords are never stored as plain text. They are salted and hashed with PBKDF2, and database queries are parameterized.
- **Clear names and comments** so the code is easy to read and change later.
- **Reuse.** The grid rows come from one layout file (`item_weight_row.xml`), and the same code path is used for adding and editing weights.

## 4. Testing

I tested in Android Studio. I built the project and confirmed it compiled successfully (BUILD SUCCESSFUL), then ran it on the emulator to make sure the app launches and shows the login screen. In an earlier module (Module Six) I also tested a sensor app on the emulator using the virtual sensors and breakpoints to follow the code line by line.

Testing and building showed me how important it is to catch errors early. Android Studio's build messages pointed out mismatched resource names and other small mistakes that I fixed before running the app. It also taught me to check that a feature like SMS still behaves correctly when the user denies permission.

## 5. Where I innovated to overcome a challenge

The hardest part was the SMS feature. Android requires the user to give permission before an app can send texts, and the user can also say no. I solved this by asking for permission only on the SMS screen, checking the permission every time before sending, and letting the rest of the app work normally if permission is denied. The user sees a clear status message for each case. I also learned that Google Play restricts the SEND_SMS permission, so my launch plan describes safer alternatives such as an in-app notification.

## 6. Component that best shows my skills

The **database layer** (`DatabaseHelper`) best shows my skills. It includes secure password hashing, three related tables, and full create, read, update, and delete (CRUD) operations for weights and goals. It also keeps each user's data separate, and every other screen in the app depends on it working correctly.
