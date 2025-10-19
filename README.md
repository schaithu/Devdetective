DevDetective & Real-Time Messaging
This is a single-page web application that combines two powerful functionalities: a GitHub user search tool ("DevDetective") and a real-time email contact form powered by EmailJS. It's built with modern web technologies, including Bootstrap 5 for a clean, responsive layout.

Shutterstock

✨ Features
GitHub User Search:

Enter any GitHub username to fetch and display their profile information in real-time.

Dynamically updates the UI with the user's avatar, name, bio, join date, and key statistics (Repos, Followers, Following).

Includes direct links to their GitHub profile, personal website, and Twitter handle.

Provides clear error feedback for invalid or non-existent usernames.

Real-Time Email Form:

A complete contact form to send emails directly from the webpage without needing a backend server.

Uses the EmailJS service to handle the email sending process securely.

Gives the user instant visual feedback on whether the message was sent successfully or failed.

Responsive & Modern Design:

Built with Bootstrap 5, the application is fully responsive and works seamlessly on desktops, tablets, and mobile devices.

Features a clean, modern aesthetic with custom styling and a professional font.

🛠️ Technologies Used
Frontend: HTML5, CSS3, JavaScript (ES6+)

Styling: Bootstrap 5, Google Fonts (Space Mono)

APIs:

GitHub API: To fetch user profile data.

EmailJS: To send emails directly from the client-side.

🚀 Setup and Usage
Because this is a client-side application, running it is very simple. However, to enable the email functionality, you'll need to configure your own free EmailJS account.

Step 1: Get the Code
Download or clone the project files. The entire application is contained within the single index.html file.

Step 2: Set Up EmailJS
Go to EmailJS.com and create a free account.

From your dashboard, add a new email service (e.g., Gmail, Outlook).

Create a new email template. Your template must include variables to accept the form data. Use the following variable names inside double curly braces: {{user_name}}, {{user_email}}, {{to_email}}, and {{message}}.

Find your Public Key, Service ID, and Template ID from your EmailJS account dashboard.

Step 3: Configure the Code
Open the index.html file in a text editor and scroll to the <script> section at the bottom. You must replace the placeholder keys with your own.

Initialize EmailJS with your Public Key:

JavaScript

// Replace with your own EmailJS public key
emailjs.init("YOUR_PUBLIC_KEY"); 
Update the Form Submission with your Service & Template IDs:

JavaScript

// Inside the 'contact-form' event listener
// Replace with your own Service ID and Template ID
emailjs.sendForm("YOUR_SERVICE_ID", "YOUR_TEMPLATE_ID", this)
    .then(() => {
        // Success logic...
    })
    .catch((error) => {
        // Error logic...
    });
Step 4: Run the Application
Simply open the modified index.html file in any modern web browser (like Chrome, Firefox, or Edge). The application is now live and fully functional!

🔧 How It Works
GitHub Search
The search functionality uses the native JavaScript fetch API. When a user clicks the "Search" button, a GET request is sent to the GitHub API endpoint: https://api.github.com/users/{username}.

If the request is successful (HTTP status 200), the returned JSON data is used to populate the profile card elements in the DOM.

If the request fails (e.g., a 404 Not Found error), an error message is displayed to the user.

Email Form
The contact form's default submission behavior is prevented using event.preventDefault(). Instead, when the form is submitted, the emailjs.sendForm() method is called. This method securely sends the form data to the EmailJS servers, which then use your configured service and template to send the email on your behalf, all without exposing your credentials or requiring a server.
