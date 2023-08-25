<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="styles.css">
  <title>Dynamic Menu</title>
</head>
<body>
  <nav id="top-menu" class="menu">
    <!-- Dynamic menu items will be added here using JavaScript -->
  </nav>
  <script src="script.js"></script>
</body>
</html>
.menu {
  background-color: #333;
  color: white;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 10px;
}

.menu-item {
  cursor: pointer;
}
const navbar = [
  { name: 'Home', id: 'home' },
  { name: 'About', id: 'about' },
  {
    name: 'Our Products',
    id: 'product',
    child: [
      { name: 'Product 1', id: 'p1' },
      { name: 'Product 2', id: 'p2' },
      { name: 'Product 3', id: 'p3' },
      { name: 'Product 4', id: 'p4' },
    ],
  },
  { name: 'Contact Us', id: 'contact' },
];

const topMenu = document.getElementById('top-menu');

navbar.forEach(item => {
  const menuItem = document.createElement('div');
  menuItem.textContent = item.name;
  menuItem.classList.add('menu-item');

  if (item.child) {
    menuItem.addEventListener('mouseenter', () => {
      // Clear existing child items
      topMenu.querySelectorAll('.sub-menu').forEach(subMenu => {
        subMenu.remove();
      });

      // Create and append child items
      const subMenu = document.createElement('div');
      subMenu.classList.add('sub-menu');
      item.child.forEach(childItem => {
        const subMenuItem = document.createElement('div');
        subMenuItem.textContent = childItem.name;
        subMenuItem.classList.add('menu-item');
        subMenu.appendChild(subMenuItem);
      });

      topMenu.appendChild(subMenu);
    });
  }

  topMenu.appendChild(menuItem);
});

