# Final-project
sneaker-store/
├── index.html       # 主页面
├── style.css        # 样式文件
├── script.js        # 交互逻辑
└── README.md        # GitHub 说明文档

<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sneaker Hub - 专业球鞋商城</title>
    <link rel="stylesheet" href="style.css">
    <!-- 引入图标库 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>
    <!-- 导航栏 -->
    <header class="navbar">
        <div class="container">
            <div class="logo">
                <i class="fas fa-shoe-prints"></i>
                <span>Sneaker Hub</span>
            </div>
            <nav class="nav-links">
                <a href="#home">首页</a>
                <a href="#products">新品</a>
                <a href="#brands">品牌</a>
                <a href="#about">关于</a>
                <div class="cart-icon" id="cartBtn">
                    <i class="fas fa-shopping-cart"></i>
                    <span class="cart-count" id="cartCount">0</span>
                </div>
            </nav>
            <div class="menu-btn" id="menuBtn">
                <i class="fas fa-bars"></i>
            </div>
        </div>
    </header>

    <!-- 轮播横幅 -->
    <section class="banner" id="home">
        <div class="banner-content">
            <h1>限量球鞋 · 即刻拥有</h1>
            <p>正品保障 | 极速发货 | 潮流首选</p>
            <a href="#products" class="btn">立即选购</a>
        </div>
    </section>

    <!-- 产品列表 -->
    <section class="products" id="products">
        <div class="container">
            <h2 class="section-title">热门球鞋</h2>
            <div class="products-grid" id="productsGrid">
                <!-- 产品由 JS 动态渲染 -->
            </div>
        </div>
    </section>

    <!-- 购物车弹窗 -->
    <div class="cart-modal" id="cartModal">
        <div class="cart-content">
            <div class="cart-header">
                <h3>购物车</h3>
                <span class="close-cart" id="closeCart">&times;</span>
            </div>
            <div class="cart-items" id="cartItems">
                <p class="empty-cart">购物车为空</p>
            </div>
            <div class="cart-footer">
                <p>总计: <span id="totalPrice">¥0</span></p>
                <button class="checkout-btn">结算</button>
            </div>
        </div>
    </div>

    <!-- 页脚 -->
    <footer>
        <div class="container">
            <p>&copy; 2025 Sneaker Hub - 球鞋商城 版权所有</p>
        </div>
    </footer>

    <script src="script.js"></script>
</body>
</html>

/* 全局样式 */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Arial', sans-serif;
}

:root {
    --primary: #ff3c57;
    --dark: #1a1a1a;
    --light: #f5f5f5;
    --gray: #777;
}

body {
    background-color: var(--light);
    color: var(--dark);
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
}

.btn {
    display: inline-block;
    background: var(--primary);
    color: white;
    padding: 12px 24px;
    border-radius: 5px;
    text-decoration: none;
    font-weight: bold;
    transition: 0.3s;
}

.btn:hover {
    background: #e02d45;
    transform: translateY(-2px);
}

/* 导航栏 */
.navbar {
    background: white;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    position: sticky;
    top: 0;
    z-index: 100;
}

.navbar .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 20px;
}

.logo {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 24px;
    font-weight: bold;
    color: var(--primary);
}

.nav-links {
    display: flex;
    align-items: center;
    gap: 30px;
}

.nav-links a {
    text-decoration: none;
    color: var(--dark);
    font-weight: 500;
    transition: 0.3s;
}

.nav-links a:hover {
    color: var(--primary);
}

.cart-icon {
    position: relative;
    cursor: pointer;
    font-size: 20px;
}

.cart-count {
    position: absolute;
    top: -10px;
    right: -10px;
    background: var(--primary);
    color: white;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
}

.menu-btn {
    display: none;
    font-size: 24px;
    cursor: pointer;
}

/* 横幅 */
.banner {
    height: 80vh;
    background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1542291026-7eec264c27ff?ixlib=rb-4.0.3&auto=format&fit=crop&w=1500&q=80');
    background-size: cover;
    background-position: center;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: white;
}

.banner-content h1 {
    font-size: 48px;
    margin-bottom: 20px;
}

.banner-content p {
    font-size: 18px;
    margin-bottom: 30px;
}

/* 产品区域 */
.section-title {
    text-align: center;
    font-size: 32px;
    margin: 50px 0 30px;
    position: relative;
}

.section-title::after {
    content: '';
    width: 80px;
    height: 3px;
    background: var(--primary);
    display: block;
    margin: 10px auto;
}

.products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 30px;
    margin-bottom: 60px;
}

.product-card {
    background: white;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    transition: 0.3s;
}

.product-card:hover {
    transform: translateY(-10px);
}

.product-img {
    width: 100%;
    height: 250px;
    object-fit: cover;
}

.product-info {
    padding: 20px;
}

.product-name {
    font-size: 18px;
    margin-bottom: 10px;
}

.product-price {
    color: var(--primary);
    font-size: 22px;
    font-weight: bold;
    margin-bottom: 15px;
}

.add-to-cart {
    width: 100%;
    padding: 10px;
    background: var(--primary);
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-weight: bold;
    transition: 0.3s;
}

.add-to-cart:hover {
    background: #e02d45;
}

/* 购物车弹窗 */
.cart-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 1000;
}

.cart-content {
    background: white;
    width: 90%;
    max-width: 500px;
    border-radius: 10px;
    max-height: 80vh;
    overflow-y: auto;
}

.cart-header {
    padding: 20px;
    border-bottom: 1px solid #ddd;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.close-cart {
    font-size: 28px;
    cursor: pointer;
}

.cart-items {
    padding: 20px;
}

.cart-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 0;
    border-bottom: 1px solid #eee;
}

.empty-cart {
    text-align: center;
    color: var(--gray);
    padding: 20px;
}

.cart-footer {
    padding: 20px;
    border-top: 1px solid #ddd;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.checkout-btn {
    background: var(--primary);
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
}

/* 页脚 */
footer {
    background: var(--dark);
    color: white;
    text-align: center;
    padding: 30px 0;
}

/* 响应式 */
@media (max-width: 768px) {
    .nav-links {
        display: none;
    }
    .menu-btn {
        display: block;
    }
    .banner-content h1 {
        font-size: 32px;
    }
}
// 球鞋产品数据
const products = [
    {
        id: 1,
        name: "Air Jordan 1 黑红",
        price: 1299,
        image: "https://images.unsplash.com/photo-1542291026-7eec264c27ff?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
    },
    {
        id: 2,
        name: "Nike Dunk 熊猫",
        price: 899,
        image: "https://images.unsplash.com/photo-1556911220-bff31c812dba?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
    },
    {
        id: 3,
        name: "Adidas Yeezy 350",
        price: 1999,
        image: "https://images.unsplash.com/photo-1584917714317-f24f2bf25cc9?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
    },
    {
        id: 4,
        name: "New Balance 990",
        price: 1199,
        image: "https://images.unsplash.com/photo-1612902367274-76169342d2b2?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
    },
    {
        id: 5,
        name: "Nike Air Max 270",
        price: 799,
        image: "https://images.unsplash.com/photo-1550307151-40006478f92e?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
    },
    {
        id: 6,
        name: "Converse 1970s",
        price: 599,
        image: "https://images.unsplash.com/photo-1612902367274-76169342d2b2?ixlib=rb-4.0.3&auto=format&fit=crop&w=800&q=80"
    }
];

// DOM 元素
const productsGrid = document.getElementById('productsGrid');
const cartBtn = document.getElementById('cartBtn');
const cartModal = document.getElementById('cartModal');
const closeCart = document.getElementById('closeCart');
const cartItems = document.getElementById('cartItems');
const cartCount = document.getElementById('cartCount');
const totalPrice = document.getElementById('totalPrice');

// 购物车数组
let cart = JSON.parse(localStorage.getItem('cart')) || [];

// 渲染产品
function renderProducts() {
    productsGrid.innerHTML = '';
    products.forEach(product => {
        const productCard = document.createElement('div');
        productCard.className = 'product-card';
        productCard.innerHTML = `
            <img src="${product.image}" alt="${product.name}" class="product-img">
            <div class="product-info">
                <h3 class="product-name">${product.name}</h3>
                <p class="product-price">¥${product.price}</p>
                <button class="add-to-cart" onclick="addToCart(${product.id})">加入购物车</button>
            </div>
        `;
        productsGrid.appendChild(productCard);
    });
}

// 添加到购物车
function addToCart(productId) {
    const product = products.find(item => item.id === productId);
    const existingItem = cart.find(item => item.id === productId);

    if (existingItem) {
        existingItem.quantity += 1;
    } else {
        cart.push({ ...product, quantity: 1 });
    }

    updateCart();
    alert(`${product.name} 已加入购物车`);
}

// 更新购物车
function updateCart() {
    localStorage.setItem('cart', JSON.stringify(cart));
    renderCart();
    updateCartCount();
}

// 渲染购物车
function renderCart() {
    if (cart.length === 0) {
        cartItems.innerHTML = '<p class="empty-cart">购物车为空</p>';
        totalPrice.textContent = '¥0';
        return;
    }

    cartItems.innerHTML = '';
    let total = 0;

    cart.forEach(item => {
        const itemTotal = item.price * item.quantity;
        total += itemTotal;

        const cartItem = document.createElement('div');
        cartItem.className = 'cart-item';
        cartItem.innerHTML = `
            <div>
                <p>${item.name}</p>
                <p>¥${item.price} x ${item.quantity}</p>
            </div>
            <p>¥${itemTotal}</p>
        `;
        cartItems.appendChild(cartItem);
    });

    totalPrice.textContent = `¥${total}`;
}

// 更新购物车数量
function updateCartCount() {
    const count = cart.reduce((sum, item) => sum + item.quantity, 0);
    cartCount.textContent = count;
}

// 购物车弹窗控制
cartBtn.addEventListener('click', () => {
    cartModal.style.display = 'flex';
});

closeCart.addEventListener('click', () => {
    cartModal.style.display = 'none';
});

window.addEventListener('click', (e) => {
    if (e.target === cartModal) {
        cartModal.style.display = 'none';
    }
});

// 初始化
renderProducts();
updateCart();
