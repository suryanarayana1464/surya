<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login Page</title>
    <!-- Latest compiled and minified CSS -->
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
    <!-- jQuery library -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
    <!-- Latest compiled JavaScript -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>
    <center>
        <h1><u>Login Page</u></h1>

        <!-- Error message (Initially hidden) -->
        <div id="error-message" class="alert alert-danger" style="display:none;" role="alert">
            Invalid username or password.
        </div>

        <!-- Login Form -->
        Username: <input type="text" id="username" required><p></p>
        Password: <input type="password" id="password" required><p></p>
        <button type="button" class="btn btn-info" onclick="validateLogin()">Login</button>

        <!-- Success message (Initially hidden) -->
        <div id="success-message" class="alert alert-success" style="display:none;" role="alert">
            Login successful! Redirecting...
        </div>
    </center>

    <script>
        const validUsers = [
        { username: "bhaskar", password: "0474", redirectUrl: "https://www.flipkart.com/" },
        { username: "murali", password: "1422", redirectUrl: "https://www.youtube.com/" },
        { username: "surya", password: "1464", redirectUrl: "https://suryanarayana1464.github.io/surya-profile/" },
        { username: "sairam", password: "42c6", redirectUrl: "https://www.amazon.in/" }
        ];

// Validate the login credentials
        function validateLogin() {
        const username = document.getElementById("username").value;
        const password = document.getElementById("password").value;

        let validLogin = false;
        let redirectUrl = "";

        // Input validation
        if (!username || !password) {
            document.getElementById("error-message").textContent = "Please enter both username and password.";
            document.getElementById("error-message").style.display = "block";
            return;  // Stop execution if inputs are empty
        }

            // Loop through valid users and check if the credentials match
        for (let i = 0; i < validUsers.length; i++) {
            if (username === validUsers[i].username && password === validUsers[i].password) {
                validLogin = true;
                redirectUrl = validUsers[i].redirectUrl;  // Store the redirect URL
                break;  // Exit the loop once a match is found
        }
        }

        // If valid login, show success message and redirect
        if (validLogin) {
            document.getElementById("error-message").style.display = "none";
            document.getElementById("success-message").style.display = "block";

            // Redirect to the user-specific URL after 2 seconds
            setTimeout(function() {
                window.location.href = redirectUrl;
            }, 2000);
        } else {
            // If invalid login, show error message
            document.getElementById("error-message").textContent = "Invalid username or password.";
            document.getElementById("error-message").style.display = "block";
        }
    }

    </script>
</body>
</html>
