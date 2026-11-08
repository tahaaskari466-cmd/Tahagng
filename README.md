
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GUN GOLD SHOP</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  background: #080808;
  color: white;
  font-family: Tahoma, sans-serif;
}

header {
  text-align: center;
  padding: 28px 10px;
  background: #171717;
  border-bottom: 2px solid gold;
}

header h1 {
  color: gold;
  font-size: 30px;
}

header p {
  color: #aaa;
}

.hero {
  text-align: center;
  padding: 55px 15px;
  background: linear-gradient(140deg, #3b3008, #090909);
}

.hero h2 {
  color: gold;
  font-size: 27px;
}

.hero p {
  line-height: 2;
  color: #ddd;
}

.container {
  max-width: 850px;
  margin: auto;
  padding: 20px;
}

.section-title {
  color: gold;
  text-align: center;
  margin: 30px 0;
}

.products {
  display: grid;
  grid-template-columns: repeat(auto-fit,minmax(220px,1fr));
  gap: 18px;
}

.product {
  background: #191919;
  border: 1px solid #8b7000;
  border-radius: 15px;
  text-align: center;
  padding: 25px;
}

.gun {
  font-size: 55px;
}

.price {
  color: gold;
  font-size: 22px;
  font-weight: bold;
  margin: 20px 0;
}

button {
  background: gold;
  color: black;
  border: 0;
  border-radius: 9px;
  padding: 13px 22px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  background: #ffe66d;
}

.order {
  background: #191919;
  border: 1px solid #8b7000;
  border-radius: 15px;
  padding: 25px;
  margin-top: 35px;
}

input, select {
  display: block;
  width: 100%;
  padding: 14px;
  margin: 12px 0;
  background: #292929;
  border: 1px solid #555;
  color: white;
  border-radius: 8px;
  font-size: 15px;
}

.total {
  color: gold;
  font-size: 21px;
  margin: 20px 0;
}

#message {
  color: #aaffaa;
  line-height: 2;
  margin-top: 15px;
}

footer {
  text-align: center;
  padding: 25px;
  margin-top: 40px;
  background: #171717;
  color: #888;
}
</style>
</head>

<body>

<header>
  <h1>GUN GOLD SHOP</h1>
  <p>فروشگاه خدمات گلد گان کالاف دیوتی موبایل</p>
</header>

<section class="hero">
  <h2>گان‌هات رو طلایی کن!</h2>
  <p>هر گان فقط ۳۰۰ هزار تومان</p>
</section>

<div class="container">

  <h2 class="section-title">خدمات ما</h2>

  <div class="products">
    <div class="product">
      <div class="gun">🔫</div>
      <h3>Gold Camo</h3>
      <p>خدمات گلد کردن گان</p>
      <div class="price">۳۰۰٬۰۰۰ تومان</div>
      <button onclick="selectOrder()">ثبت سفارش</button>
    </div>
  </div>

  <div class="order" id="order">
    <h2 class="section-title">ثبت درخواست</h2>

    <form onsubmit="submitOrder(event)">
      <input id="name" type="text"
        placeholder="نام شما" required>

      <input id="gunName" type="text"
        placeholder="نام گان موردنظر" required>

      <label for="quantity">تعداد گان:</label>
      <input id="quantity" type="number"
        min="1" max="50" value="1" required>

      <div class="total" id="total">
        مبلغ کل: ۳۰۰٬۰۰۰ تومان
      </div>

      <button type="submit">ثبت درخواست</button>
    </form>

    <div id="message"></div>
  </div>

</div>

<footer>
  <h3>GUN GOLD SHOP</h3>
  <p>تمام حقوق محفوظ است.</p>
</footer>

<script>
const price = 300000;

const quantity = document.getElementById("quantity");
const total = document.getElementById("total");

function money(number) {
  return number.toLocaleString("fa-IR");
}

function updatePrice() {
  let count = Number(quantity.value);

  if (!Number.isFinite(count) || count < 1) {
    count = 1;
  }

  if (count > 50) count = 50;

  total.textContent =
    "مبلغ کل: " + money(count * price) + " تومان";
}

quantity.addEventListener("input", updatePrice);

function selectOrder() {
  document.getElementById("order").scrollIntoView({
    behavior: "smooth"
  });
}

function submitOrder(event) {
  event.preventDefault();

  const name = document.getElementById("name").value;
  const gun = document.getElementById("gunName").value;
  const count = Number(quantity.value);

  if (!Number.isInteger(count) || count < 1 || count > 50) {
    alert("تعداد باید بین ۱ تا ۵۰ باشد.");
    return;
  }

  const amount = count * price;

  document.getElementById("message").textContent =
    "درخواست نمایشی شما آماده شد، " + name +
    " | گان: " + gun +
    " | تعداد: " + count +
    " | مبلغ: " + money(amount) + " تومان";
}

updatePrice();
</script>

</body>
</html>
