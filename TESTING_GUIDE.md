# Testing Guide for Multiple Images & Checkout Features

## 🧪 Quick Testing Steps

### Part 1: Testing Multiple Image Upload (Admin Panel)

1. **Login to Admin Panel**
   - Go to: `admin-login.html`
   - Username: `admin`
   - Password: `admin123`
   - (Alternative: sunil/sunil@123)

2. **Add Product with Multiple Images**
   - Click "Dashboard" tab
   - Scroll down to "Products" section
   - Click "Add New Product" button
   - Fill in product details:
     - Name: "Gold Ring Design"
     - Category: "rings"
     - Price: "5000"
     - Stock: "10"
     - Description: "Beautiful gold ring with multiple designs"
   - **Click on the image input field**
   - **Select 3-5 images from your computer** (hold Ctrl to select multiple)
   - You should see thumbnails preview below the input
   - Click "Save Product"
   - Alert will show "Product saved successfully!"

3. **Edit Product & Verify Images**
   - In Products table, find your newly added product
   - Click "Edit" button
   - Scroll down to see image gallery
   - You should see all 3-5 image thumbnails displayed
   - Each image shows a "Remove" button (red, won't actually delete yet)
   - Click "Save" without adding new images
   - Images should remain the same

### Part 2: Testing Product Gallery with Multiple Images

1. **View Products in Gallery**
   - Go to: `gallery.html`
   - You should see products displayed as cards
   - For the product you created with 3+ images:
     - Primary image (first one) should display
     - **Look for small badge showing image count** (e.g., "📷 3" or "🖼️ 3")

2. **Test Image Zoom with Carousel**
   - Click on the product image card
   - Zoom modal should open with the first image
   - **For products with multiple images**, you should see:
     - ◀ Left arrow button
     - ▶ Right arrow button  
     - Counter at bottom showing "1 / 3" (or however many images)
   - Click the **right arrow** → next image should load, counter updates to "2 / 3"
   - Click the **left arrow** → goes back to previous image, counter updates to "1 / 3"
   - Click the **left arrow again on image 1** → wraps to last image "3 / 3"
   - Press **Escape or click outside** → modal closes

3. **Test Single Image Functionality**
   - Add another product with just **1 image**
   - In gallery, it should NOT show image count badge
   - Click to zoom → should open modal with just the image, no carousel arrows

### Part 3: Testing Shipping Address Checkout

1. **Add Items to Cart**
   - From gallery.html, add 2-3 products to cart
   - Click cart icon in header

2. **Review Cart**
   - Should see items list with quantities
   - Subtotal, Tax, Total should calculate correctly
   - Click "Proceed to Checkout" button

3. **Fill Shipping Form**
   - **Progress indicator** at top should show: ✓ Cart → ⊙ Shipping → ○ Confirmation
   - Fill in all required fields (*):
     - **Full Name**: "John Doe"
     - **Email**: "john@example.com"
     - **Phone**: "+91 9876543210"
     - **Street Address**: "123 Main Street, Apt 4B"
     - **City**: "Mumbai"
     - **State/Province**: "Maharashtra"
     - **Postal Code**: "400001"
     - **Country**: "India" (pre-filled)

4. **Review Order Summary**
   - Should see all your items listed with prices
   - Subtotal, Tax, and Total should be visible
   - Click "Continue to Order"

5. **Expected Behavior on Submit**
   - Form validates all fields
   - If any field is empty → shows red error message: "Please fill in all required fields"
   - If email is invalid (like "noatsign.com") → error message: "Please enter a valid email address"
   - If phone is invalid (less than 10 digits) → error may appear
   - If all valid → redirected to confirmation page

### Part 4: Testing Order Confirmation

1. **Confirmation Page Display**
   - Should see ✅ success icon with "Order Confirmed!" message
   - **Progress indicator** shows: ✓ Cart → ✓ Shipping → ✓ Confirmation
   - Order number should display like "Order #1703261234"

2. **Order Details**
   - All customer information filled in from shipping form
   - All items listed with quantities and prices
   - **Shipping Address section** shows complete formatted address
   - **Price Summary** shows:
     - Subtotal amount
     - Tax (5%)
     - Total Amount
   - Status shows "Pending" badge

3. **Next Steps Message**
   - Info box displays WhatsApp notification info
   - **Browser may show WhatsApp prompt** (especially on mobile)
   - WhatsApp message should contain:
     - Order #, Customer name, Email, Phone
     - Shipping address
     - All items with quantities
     - Price breakdown

4. **Navigation Buttons**
   - "Continue Shopping" button → goes back to gallery.html
   - "Back to Home" button → goes to index.html

### Part 5: Testing Admin Order Tracking

1. **Check Order in Admin Panel**
   - Go back to admin.html
   - Click "Orders" tab
   - Your new order should appear in the orders table
   - Click "View Details" to see full order information
   - Should include:
     - Shipping address
     - All items ordered
     - Payment status

2. **Check Customer in Admin**
   - Click "Customers" tab
   - You should see the customer you just created
   - Order count: "1"
   - Total Spent: "₹[total amount]"

### Part 6: Testing Mobile Responsiveness

1. **On Mobile Device or Browser DevTools (F12)**
   - Toggle device toolbar (Ctrl+Shift+M)
   - Set to iPhone 12, Galaxy S21, or iPad

2. **Check Each Page**
   - **checkout-shipping.html**:
     - Hamburger menu appears ☰
     - Form fields stack vertically
     - Image input works
     - Buttons full width
   
   - **order-confirmation.html**:
     - Hamburger menu appears ☰
     - Confirmation message readable
     - Order details formatted for small screens
     - Buttons stack vertically

3. **Header Navigation**
   - Click hamburger menu ☰
   - Menu slides down with all navigation links
   - Can close by clicking again or selecting a link

## ✅ Expected Test Results Summary

| Feature | Status | Notes |
|---------|--------|-------|
| Multiple image upload | ✅ | 3+ images preview in admin |
| Image gallery display | ✅ | First image shown, image count badge |
| Zoom carousel | ✅ | Arrows, counter, wrap-around |
| Shipping form | ✅ | All fields required, validation works |
| Order confirmation | ✅ | Shows complete details and address |
| Admin tracking | ✅ | Orders and customers listed |
| Mobile responsive | ✅ | Hamburger menu, stacked layout |
| WhatsApp integration | ✅ | Message contains order details |

## 🐛 Troubleshooting

**Issue**: Images not saving
- **Solution**: Check browser localStorage limit (usually 5-10MB)
- Large images consume more space

**Issue**: Carousel buttons not showing
- **Solution**: Make sure product has 2+ images
- Products with 1 image don't show carousel

**Issue**: Form not validating
- **Solution**: Check browser console (F12 → Console)
- Look for JavaScript errors

**Issue**: WhatsApp not opening
- **Solution**: May be blocked by popup blocker
- Allow popups for this website
- Check WhatsApp Web is accessible

**Issue**: Mobile menu not working
- **Solution**: Check if hamburger icon is visible (at 768px or below)
- Click the ☰ icon, not empty space

## 📞 Contact for Support
- Phone: +91 6350217120
- Email: gupspbnnp@gmail.com

---

**Testing Date**: ________________
**Tester Name**: ________________
**Test Result**: ✅ PASS / ❌ FAIL
