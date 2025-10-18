<!DOCTYPE html>

<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>日ごとの金額計算ツール</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <style>
    body {
      font-family: "Segoe UI", "Hiragino Sans", sans-serif;
      margin: 20px;
      background: linear-gradient(135deg, #f4f6f8, #e9ecef);
      color: #333;
    }

    h1 {
      text-align: center;
      margin-bottom: 20px;
      color: #2c3e50;
    }

    .day {
      background: #fff;
      padding: 15px;
      border-radius: 16px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      margin-bottom: 20px;
    }

    label {
      display: inline-block;
      width: 70px;
      font-weight: bold;
    }

    input {
      width: 80px;
      padding: 6px;
      text-align: right;
      border-radius: 8px;
      border: 1px solid #ccc;
      margin: 4px;
    }

    button {
      display: inline-block;
      margin: 10px 5px;
      padding: 10px 18px;
      background-color: #007bff;
      color: #fff;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      transition: 0.2s;
    }

    button:hover {
      background-color: #0056b3;
    }

    .result {
      background: #fff;
      padding: 15px;
      border-radius: 16px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      font-size: 17px;
    }

    .subresult {
      margin-top: 10px;
      font-size: 15px;
      color: #555;
    }

    .day-title {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 8px;
      color: #007bff;
    }

    hr {
      margin: 15px 0;
    }
  </style>
</head>
<body>

  <h1>日ごとの金額計算ツール</h1>

  <div id="inputs">
    <div class="day">
      <div class="day-title">1日目</div>
      <label>10000円:</label><input type="number" class="yen10000" min="0"><br>
      <label>5000円:</label><input type="number" class="yen5000" min="0"><br>
      <label>1000円:</label><input type="number" class="yen1000" min="0"><br>
      <label>500円:</label><input type="number" class="yen500" min="0"><br>
      <label>100円:</label><input type="number" class="yen100" min="0"><br>
      <label>50円:</label><input type="number" class="yen50" min="0"><br>
      <label>10円:</label><input type="number" class="yen10" min="0"><br>
      <label>5円:</label><input type="number" class="yen5" min="0"><br>
      <label>1円:</label><input type="number" class="yen1" min="0"><br>
    </div>
  </div>

  <button onclick="addDay()">日を追加</button>
  <button onclick="calculate()">計算する</button>

  <div id="result" class="result"></div>

  <script>
    let dayCount = 1;

    const denominations = [
      { label: "10000円", class: "yen10000", value: 10000 },
      { label: "5000円", class: "yen5000", value: 5000 },
      { label: "1000円", class: "yen1000", value: 1000 },
      { label: "500円", class: "yen500", value: 500 },
      { label: "100円", class: "yen100", value: 100 },
      { label: "50円", class: "yen50", value: 50 },
      { label: "10円", class: "yen10", value: 10 },
      { label: "5円", class: "yen5", value: 5 },
      { label: "1円", class: "yen1", value: 1 }
    ];

    // 日を追加
    function addDay() {
      dayCount++;
      const div = document.createElement("div");
      div.classList.add("day");
      div.innerHTML = `<div class="day-title">${dayCount}日目</div>`;
      denominations.forEach(d => {
        div.innerHTML += `
          <label>${d.label}:</label>
          <input type="number" class="${d.class}" min="0"><br>`;
      });
      document.getElementById("inputs").appendChild(div);
    }

    // 計算
    function calculate() {
      const allDays = document.querySelectorAll(".day");
      let totals = {};
      denominations.forEach(d => totals[d.class] = 0);

      let grandTotal = 0;
      let resultHTML = "";

      allDays.forEach((day, i) => {
        let dayTotal = 0;
        let details = "";

        denominations.forEach(d => {
          const num = Number(day.querySelector(`.${d.class}`).value) || 0;
          const subtotal = num * d.value;
          totals[d.class] += num;
          dayTotal += subtotal;
          if (num > 0) {
            details += `${d.label}: ${num}枚 (${subtotal.toLocaleString()}円)<br>`;
          }
        });

        resultHTML += `<div class="subresult">
          <b>${i + 1}日目</b><br>${details || "入力なし"}<b>合計:</b> ${dayTotal.toLocaleString()}円
        </div><hr>`;
        grandTotal += dayTotal;
      });

      // 合計まとめ
      let summary = "";
      denominations.forEach(d => {
        const totalPieces = totals[d.class];
        if (totalPieces > 0) {
          summary += `${d.label} × ${totalPieces}枚 = ${(totalPieces * d.value).toLocaleString()}円<br>`;
        }
      });

      document.getElementById("result").innerHTML = `
        <strong>総合計：</strong><br>
        ${summary}<br>
        <b style="font-size:18px;">合計金額：${grandTotal.toLocaleString()}円</b>
      `;
    }
  </script>

</body>
</html>
