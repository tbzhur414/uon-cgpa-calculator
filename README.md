UON CGPA Calculator Android App
Overview
The UON CGPA Calculator is an offline Android application designed for University of Narowal students to calculate their Grade Point Average (GPA) and Cumulative Grade Point Average (CGPA). This app is a port of the web-based CGPA calculator (originally hosted at https://tbzhur414.github.io/cgpa-calculator/), converted into a native Android app using a WebView to ensure offline functionality. The app allows students to input course grades and credit hours to compute GPA for a single semester or CGPA across multiple semesters, following the University of Narowal's grading system.
Features

GPA Calculator: Calculate semester GPA by entering course grades and credit hours.
CGPA Calculator: Compute cumulative GPA across multiple semesters.
Offline Access: All functionality works without an internet connection, as web assets are bundled in the app.
UON Grading System: Displays the University of Narowal's grading chart and academic standards.
Responsive Design: Inherits the web app's responsive UI, optimized for mobile screens via WebView.
User-Friendly Interface: Simple input fields and validation for accurate calculations.

Tech Stack

Android Platform: Built using Android Studio with Kotlin (or Java, depending on your choice).
WebView: Embeds the original HTML, CSS, and JavaScript files from the web app.
Assets: Local HTML, CSS, and JS files stored in the app's assets folder for offline use.
Android SDK: Minimum API 21 (Android 5.0) for broad device compatibility.

Prerequisites
To build or modify this project, you need:

Android Studio: Download from developer.android.com/studio.
Project Files: The original web app files (index.html, CSS, JS, etc.) and this Android project.
Basic Knowledge: Familiarity with Android Studio basics (e.g., running an app on an emulator/device).

Installation and Setup

Clone or Download the Project:

Clone this repository or download the project files.
Ensure the web app files (HTML, CSS, JS) are included in the app/src/main/assets folder.


Open in Android Studio:

Launch Android Studio and select Open an existing project.
Navigate to the project folder and open it.


Add Web App Files:

Copy your web app files (e.g., index.html, (css/, js/)) into app/src/main/assets.
Maintain the folder structure (e.g., assets/js/script.js) to match relative paths in your HTML.


Configure WebView:

Ensure app/src/main/res/layout/activity_main.xml contains a WebView:<WebView
    android:id="@+id/webView"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />


Verify MainActivity.kt (or .java) loads the HTML file and enables JavaScript:val webView: WebView = findViewById(R.id.webView)
webView.settings.javaScriptEnabled = true
webView.settings.domStorageEnabled = true
webView.settings.allowFileAccess = true
webView.loadUrl("file:///android_asset/index.html")




Build and Run:

Connect an Android device (with USB debugging enabled) or use an emulator.
Click Run > Run 'app' in Android Studio.
Test the app to ensure GPA/CGPA calculations.


Generate APK:

Go to Build > Build Bundle(s)/APK(s) > Build APK to create a debug APK.
For release (e.g., Google Play), use Build > Generate Signed Bundle/APK.



Project Structure
UON-CGPA-Calculator/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── assets/                # Web app files (index.html, (css/, js/ ,Merged in html file))
│   │   │   ├── java/.../MainActivity.kt  # WebView setup and logic
│   │   │   ├── res/
│   │   │   │   ├── layout/activity_main.xml  # WebView layout
│   │   │   │   ├── mipmap/ic_launcher/       # App icon
│   │   │   │   ├── values/strings.xml        # App name and strings
│   │   │   ├── AndroidManifest.xml           # App permissions and config
│   ├── build.gradle                          # App dependencies and config
├── build.gradle                             # Project-level config
├── README.md                                # This file

Usage

GPA Calculation: Input course grades (e.g., A+, B) and credit hours for a semester to compute GPA.
CGPA Calculation: Enter semester GPAs to calculate cumulative performance.
Grading System Reference: View the UON grading chart within the app.

Debugging Tips

White Screen: Check the loadUrl path in MainActivity (e.g., file:///android_asset/index.html) and ensure files are in assets.
JavaScript Errors: Enable WebView console logs:webView.webChromeClient = object : WebChromeClient() {
    override fun onConsoleMessage(consoleMessage: ConsoleMessage?): Boolean {
        Log.d("WebView", consoleMessage?.message())
        return true
    }
}


Path Issues: Verify relative paths in HTML (e.g., <script src="js/script.js">) match the assets folder structure.

Future Improvements

Add a native Android UI for better performance (replacing WebView with Kotlin/Java logic).
Implement data persistence (e.g., Room database) to save past calculations.
Add export functionality to share GPA/CGPA results via email or PDF.
Enhance with Android-specific features like notifications for academic goals.

About the Developer
Hur Abbas RanaGraduate from University of Narowal (BS Computer Science).A web developer and data analyst skilled in HTML, CSS, JavaScript, MySQL, and Power BI, with experience in sales coordination and digital marketing at Alshafi Group Global. Passionate about creating tools to empower students and drive business growth.
License
This project is licensed under the MIT License. See the LICENSE file for details.
