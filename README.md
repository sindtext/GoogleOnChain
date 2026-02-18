# GoogleOnChain
inGame Google Auth non-custodial Wallet 

## Google On Chain ##

!! This For Unity Android Project
!! You must have android studio installed

A. Unity Package
1. Install unity 6 & Android Depedency
2. Open GoogleOnChain.unitypackage

B. Firebase Console Setup
1. Go to the Firebase Console and create a new project.
2. Register your App (Android):
Click the Android icon to add an app.
a. Package Name: Must match your Android Unity project (e.g., com.company.gamename).
b. SHA-1 Fingerprint (Crucial): You cannot skip this.
>>> Switch project to android => Player Setting => Publishing Setting
>>> Keystore Manager => Keystore... => Create New => Anywhere
>>> Set password and everythings needed
>>> Open your terminal/command prompt.

Run this command (use your password):
"YOUR\KEYTOOL\LOCATION\keytool.exe" -list -v -keystore "YOUR\KEYSTORE\LOCATION\keystorename.keystore" -alias keystorealias (Windows)

>>> Copy the SHA1 value and paste it into Firebase [Project Overview => General => Add Fingerprint].
c. Download google-services.json and put it in your Unity Assets folder.
3. Enable Google Sign-In:
>>> In Firebase Console -> Authentication -> Sign-in method.
>>> Enable Google.
>>> Note the "Web Client ID": You will need this string later in Unity.
4. Enable Firebase Database
>>> In Firebase Console -> Firestore & Realtime Database-> Create Database.

C. Unity Installation
1. Download the Firebase Unity SDK.
>>> https://firebase.google.com/download/unity
2. Import FirebaseAuth.unitypackage.
3. Download the Google Sign-In Unity Plugin.
https://github.com/googlesamples/google-signin-unity/releases
4. Import the package. [exclude the "Parse" folder]
5. Resolve Dependencies:
>>> Go to Assets -> External Dependency Manager -> Android Resolver -> Force Resolve.
6. Make an empty object named "AppManager" and Attach "GoogleLogin.cs", Input your Web Client ID in webClientId at inspector

C. Install Nethereum
1. Install the Nethereum.Unity.package via Package Manager using OpenUpm
>>> open Edit/Project Settings/Package Manager
>>> add a new Scoped Registry (or edit the existing OpenUPM entry)
>>> Name package.openupm.com
>>> URL https://package.openupm.com
>>> Scope(s) com.nethereum.unity
>>> click Save or Apply
>>> open Window/Package Manager
>>> click +
>>> select Add package by name...
>>> add com.nethereum.unity into name
>>> add 4.19.2 into version (or your preferred one)
>>> click Add
>>> open Window/Package Manager
>>> click +
>>> select Add package by name...
>>> com.unity.nuget.newtonsoft-json
>>> click Add
2. Scene Setup
>>> Attach "GoogleAuthWallet.cs" to "AppManager"
>>> Change GAME_SALT to your Super_Secret Code
>>> [optimalization] place Super_Secret Code on firebase admin and get the code temporary without save to the device.
3. Link the Event
>>> "On Login Success (String)". Click the (+) button to add a listener.
>>> Drag the AppManager object (itself) into the "None (Object)" slot.
>>> In the function dropdown, select: GoogleAuthWallet -> ReceiveUserID

D. API Compatibility Level
1. Go to Edit -> Project Settings -> Player.
2. Find the Other Settings tab.
3. Look for Api Compatibility Level.
4. Change it from .NET Standard 2.1 to .NET Framework.
5. Note: Unity might recompile scripts for a moment.
6. Try to Build.
