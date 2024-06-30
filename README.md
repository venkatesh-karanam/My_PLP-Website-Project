# My_PLP-Website-Project

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Expense Tracker & Shopping Application</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        header {
            background-color: #4CAF50;
            color: white;
            text-align: center;
            padding: 1em 0;
        }
        main {
            padding: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        table, th, td {
            border: 1px solid #ddd;
        }
        th, td {
            padding: 8px;
            text-align: left;
        }
        img {
            max-width: 100%;
            height: auto;
        }
        form {
            margin-bottom: 20px;
        }
        .product {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }
        .product img {
            margin-right: 10px;
        }
        .product-info {
            display: flex;
            flex-direction: column;
        }
        .cart-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }
        .cart-total {
            font-weight: bold;
        }
        .search-bar {
            margin-bottom: 20px;
        }
        .search-results {
            margin-top: 20px;
        }
        .filter {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Expense Tracker & Shopping Application</h1>
    </header>
    <main>
        <h2>Welcome to the Expense Tracker & Shopping App</h2>

        <!-- Register Form -->
        <h3>Register</h3>
        <form id="registerForm">
            <label for="regName">Name:</label><br>
            <input type="text" id="regName" name="name" required><br><br>
            <label for="regEmail">Email:</label><br>
            <input type="email" id="regEmail" name="email" required><br><br>
            <label for="regPhone">Phone Number:</label><br>
            <input type="tel" id="regPhone" name="phone" required><br><br>
            <label for="regPassword">Password:</label><br>
            <input type="password" id="regPassword" name="password" required><br><br>
            <input type="submit" value="Register">
        </form>

        <!-- Login Form -->
        <h3>Login</h3>
        <form id="loginForm">
            <label for="loginEmail">Email:</label><br>
            <input type="email" id="loginEmail" name="email" required><br><br>
            <label for="loginPassword">Password:</label><br>
            <input type="password" id="loginPassword" name="password" required><br><br>
            <input type="submit" value="Login">
        </form>

        <!-- Password Reset Form -->
        <h3>Reset Password</h3>
        <form id="resetPasswordForm">
            <label for="resetEmail">Email:</label><br>
            <input type="email" id="resetEmail" name="email" required><br><br>
            <input type="submit" value="Reset Password">
        </form>

        <!-- Profile Management Form -->
        <h3>Profile Management</h3>
        <form id="profileForm">
            <label for="profileName">Name:</label><br>
            <input type="text" id="profileName" name="name" required><br><br>
            <label for="profileEmail">Email:</label><br>
            <input type="email" id="profileEmail" name="email" required><br><br>
            <label for="profilePhone">Phone Number:</label><br>
            <input type="tel" id="profilePhone" name="phone" required><br><br>
            <input type="submit" value="Update Profile">
        </form>

        <h3>User Information</h3>
        <table id="userInfoTable">
            <tr>
                <th>Name</th>
                <th>Email</th>
                <th>Phone Number</th>
            </tr>
        </table>

        <h3>Shopping Cart</h3>
        <div id="cart">
            <div class="cart-items"></div>
            <div class="cart-total">Total: $0.00</div>
            <button id="checkoutBtn">Checkout</button>
        </div>

        <h3>Product Categories</h3>
        <select id="categoryFilter">
            <option value="all">All</option>
            <option value="electronics">Electronics</option>
            <option value="clothing">Clothing</option>
            <option value="home">Home</option>
        </select>

        <h3>Search Products</h3>
        <input type="text" id="searchInput" placeholder="Search products...">
        <button id="searchBtn">Search</button>
        <div class="search-results"></div>

        <h3>Products</h3>
        <div class="product-list">
            <div class="product" data-category="electronics">
                <img src="https://via.placeholder.com/100" alt="Product Image">
                <div class="product-info">
                    <h4>Product 1</h4>
                    <p>Category: Electronics</p>
                    <p>Price: $100</p>
                    <button class="add-to-cart">Add to Cart</button>
                </div>
            </div>
            <div class="product" data-category="clothing">
                <img src="https://via.placeholder.com/100" alt="Product Image">
                <div class="product-info">
                    <h4>Product 2</h4>
                    <p>Category: Clothing</p>
                    <p>Price: $50</p>
                    <button class="add-to-cart">Add to Cart</button>
                </div>
            </div>
            <div class="product" data-category="home">
                <img src="https://via.placeholder.com/100" alt="Product Image">
                <div class="product-info">
                    <h4>Product 3</h4>
                    <p>Category: Home</p>
                    <p>Price: $30</p>
                    <button class="add-to-cart">Add to Cart</button>
                </div>
            </div>
        </div>

        <h3>Product Reviews</h3>
        <div id="reviews">
            <h4>Product 1 Reviews</h4>
            <input type="text" id="reviewInput" placeholder="Leave a review...">
            <button id="submitReview">Submit Review</button>
            <div class="reviews-list"></div>
        </div>

        <h3>Wishlist</h3>
        <div id="wishlist"></div>

        <h3>Order History</h3>
        <div id="orderHistory"></div>

        <h3>Inventory Management</h3>
        <div id="inventory"></div>
    </main>

    <script>
        // Simulated backend using localStorage
        function getUsers() {
            return JSON.parse(localStorage.getItem('users')) || [];
        }

        function saveUser(user) {
            const users = getUsers();
            users.push(user);
            localStorage.setItem('users', JSON.stringify(users));
        }

        function findUserByEmail(email) {
            return getUsers().find(user => user.email === email);
        }

        function getCurrentUser() {
            return JSON.parse(localStorage.getItem('currentUser'));
        }

        function setCurrentUser(user) {
            localStorage.setItem('currentUser', JSON.stringify(user));
        }

        function addToCart(product) {
            const cart = JSON.parse(localStorage.getItem('cart')) || [];
            cart.push(product);
            localStorage.setItem('cart', JSON.stringify(cart));
            updateCart();
        }

        function updateCart() {
            const cart = JSON.parse(localStorage.getItem('cart')) || [];
            const cartItemsContainer = document.querySelector('.cart-items');
            cartItemsContainer.innerHTML = '';
            let total = 0;
            cart.forEach(item => {
                total += item.price;
                const cartItem = document.createElement('div');
                cartItem.classList.add('cart-item');
                cartItem.innerHTML = `
                    <span>${item.name}</span>
                    <span>$${item.price}</span>
                `;
                cartItemsContainer.appendChild(cartItem);
            });
            document.querySelector('.cart-total').innerText = `Total: $${total.toFixed(2)}`;
        }

        document.getElementById('registerForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const name = document.getElementById('regName').value;
            const email = document.getElementById('regEmail').value;
            const phone = document.getElementById('regPhone').value;
            const password = document.getElementById('regPassword').value;

            const user = { name, email, phone, password };
            saveUser(user);
            alert('Registration successful');
        });

        document.getElementById('loginForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;

            const user = findUserByEmail(email);
            if (user && user.password === password) {
                alert('Login successful');
                setCurrentUser(user);
                displayUserInfo();
            } else {
                alert('Invalid credentials');
            }
        });

        document.getElementById('resetPasswordForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const email = document.getElementById('resetEmail').value;

            const user = findUserByEmail(email);
            if (user) {
                // Simulate password reset
                alert('Password reset link sent to ' + email);
            } else {
                alert('User not found');
            }
        });

        document.getElementById('profileForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const name = document.getElementById('profileName').value;
            const email = document.getElementById('profileEmail').value;
            const phone = document.getElementById('profilePhone').value;

            const currentUser = getCurrentUser();
            if (currentUser) {
                currentUser.name = name;
                currentUser.email = email;
                currentUser.phone = phone;
                setCurrentUser(currentUser);
                alert('Profile updated');
                displayUserInfo();
            } else {
                alert('No user logged in');
            }
        });

        function displayUserInfo() {
            const currentUser = getCurrentUser();
            if (currentUser) {
                const table = document.getElementById('userInfoTable');
                table.innerHTML = `
                    <tr>
                        <th>Name</th>
                        <th>Email</th>
                        <th>Phone Number</th>
                    </tr>
                    <tr>
                        <td>${currentUser.name}</td>
                        <td>${currentUser.email}</td>
                        <td>${currentUser.phone}</td>
                    </tr>
                `;
            }
        }

        document.querySelectorAll('.add-to-cart').forEach(button => {
            button.addEventListener('click', function() {
                const productElement = this.closest('.product');
                const name = productElement.querySelector('h4').innerText;
                const price = parseFloat(productElement.querySelector('p:nth-child(3)').innerText.replace('Price: $', ''));
                addToCart({ name, price });
            });
        });

        document.getElementById('searchBtn').addEventListener('click', function() {
            const searchInput = document.getElementById('searchInput').value.toLowerCase();
            const products = document.querySelectorAll('.product');
            const resultsContainer = document.querySelector('.search-results');
            resultsContainer.innerHTML = '';
            products.forEach(product => {
                const name = product.querySelector('h4').innerText.toLowerCase();
                if (name.includes(searchInput)) {
                    resultsContainer.appendChild(product.cloneNode(true));
                }
            });
        });

        document.getElementById('categoryFilter').addEventListener('change', function() {
            const category = this.value;
            const products = document.querySelectorAll('.product');
            products.forEach(product => {
                if (category === 'all' || product.getAttribute('data-category') === category) {
                    product.style.display = 'block';
                } else {
                    product.style.display = 'none';
                }
            });
        });

        document.getElementById('submitReview').addEventListener('click', function() {
            const reviewInput = document.getElementById('reviewInput').value;
            const reviewsList = document.querySelector('.reviews-list');
            const reviewElement = document.createElement('div');
            reviewElement.innerText = reviewInput;
            reviewsList.appendChild(reviewElement);
            alert('Review submitted');
        });

        // Initial display update
        displayUserInfo();
        updateCart();
    </script>
</body>
</html>
