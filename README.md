<!DOCTYPE html>
<html lang="ta">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thamees Chicken Shop</title>
    <style>
        body { font-family: 'Arial', sans-serif; background-color: #f9f9f9; margin: 0; padding: 0; color: #333; }
        header { background-color: #d32f2f; color: white; text-align: center; padding: 20px; }
        header h1 { margin: 0; font-size: 24px; }
        .container { max-width: 500px; margin: 20px auto; padding: 15px; background: white; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        .product-card { border: 1px solid #ddd; padding: 15px; margin-bottom: 15px; border-radius: 6px; display: flex; justify-content: space-between; align-items: center; }
        .product-info h3 { margin: 0 0 5px 0; color: #d32f2f; }
        .product-info p { margin: 0; font-size: 14px; color: #666; }
        .controls { display: flex; align-items: center; gap: 10px; }
        .controls input { width: 50px; padding: 5px; text-align: center; }
        .form-group { margin-bottom: 15px; }
        .form-group label { display: block; margin-bottom: 5px; font-weight: bold; }
        .form-group input, .form-group textarea { width: 100%; padding: 8px; box-sizing: border-box; border: 1px solid #ccc; border-radius: 4px; }
        .order-btn { background-color: #2e7d32; color: white; border: none; padding: 12px; width: 100%; font-size: 16px; border-radius: 4px; cursor: pointer; font-weight: bold; }
        .order-btn:hover { background-color: #1b5e20; }
    </style>
</head>
<body>

    <header>
        <h1>Thamees Chicken Shop</h1>
        <p>Fresh & Quality Chicken Delivery</p>
    </header>

    <div class="container">
        <h3>பொருட்களைத் தேர்ந்தெடுக்கவும்:</h3>
        
        <!-- Product 1 -->
        <div class="product-card">
            <div class="product-info">
                <h3>பிராய்லர் சிக்கன் (Broiler Chicken)</h3>
                <p>சுத்தமான மற்றும் தரமான கறிக்கோழி</p>
            </div>
            <div class="controls">
                <input type="number" id="qty1" min="0" value="0" placeholder="Kg">
                <span>Kg</span>
            </div>
        </div>

        <!-- Product 2 -->
        <div class="product-card">
            <div class="product-info">
                <h3>பிராய்லர் சிக்கன் மசாலா (Broiler Chicken Masala)</h3>
                <p>ஸ்பெஷல் மசாலாவுடன் மரைனேட் செய்யப்பட்டது</p>
            </div>
            <div class="controls">
                <input type="number" id="qty2" min="0" value="0" placeholder="Kg">
                <span>Kg</span>
            </div>
        </div>

        <h3>உங்கள் விபரங்கள்:</h3>
        <div class="form-group">
            <label>பெயர் (Name):</label>
            <input type="text" id="custName" placeholder="உங்கள் பெயரை உள்ளிடவும்">
        </div>
        <div class="form-group">
            <label>முகவரி (Delivery Address):</label>
            <textarea id="custAddress" rows="3" placeholder="வீட்டு முகவரியை உள்ளிடவும்"></textarea>
        </div>

        <button class="order-btn" onclick="sendOrder()">WhatsApp மூலம் ஆர்டர் செய்</button>
    </div>

    <script>
        function sendOrder() {
            let qty1 = document.getElementById('qty1').value;
            let qty2 = document.getElementById('qty2').value;
            let name = document.getElementById('custName').value;
            let address = document.getElementById('custAddress').value;

            if ((qty1 <= 0 && qty2 <= 0)) {
                alert("தயவுசெய்து ஏதாவது ஒரு பொருளின் அளவைத் தேர்ந்தெடுக்கவும்!");
                return;
            }
            if (name.trim() === "" || address.trim() === "") {
                alert("தயவுசெய்து உங்கள் பெயர் மற்றும் முகவரியை உள்ளிடவும்!");
                return;
            }

            let message = `*새 New Order - Thamees Chicken Shop*%0A%0A`;
            message += `*வாடிக்கையாளர் பெயர்:* ${name}%0A`;
            message += `*முகவரி:* ${address}%0A%0A`;
            message += `*ஆர்டர் விவரங்கள்:*%0A`;
            
            if (qty1 > 0) {
                message += `- பிராய்லர் சிக்கன்: ${qty1} Kg%0A`;
            }
            if (qty2 > 0) {
                message += `- பிராய்லர் சிக்கன் மசாலா: ${qty2} Kg%0A`;
            }

            let whatsappNumber = "94741151245"; // Sri Lanka Country code included
            let url = `https://wa.me/${whatsappNumber}?text=${message}`;
            
            window.open(url, '_blank');
        }
    </script>

</body>
</html>
