# 🎧 基於 Session 的 Top-N 推薦資料前處理

本專案提供一個資料前處理流程，針對 **基於 Session 的推薦系統**，提取並清理每個使用者會話中最常出現的前五項項目（如歌曲），以利後續模型訓練或分析使用。

---

## 📌 專案目的

將原始使用者互動資料轉換為結構化格式，提取每個 session 中出現頻率最高的前五個項目（top1 ~ top5），並處理缺失值，確保資料乾淨、穩定，能直接用於推薦系統建模或行為分析。

---

## 🔧 資料處理流程

1. **分群與統計**
   利用 `groupby` 與 `size()` 統計每個 session 中各項目（如歌曲）的出現次數。

2. **排序與擷取**
   依照每個 session 的出現次數排序，擷取前五名。

3. **轉置與命名**
   使用 `pivot` 將資料轉為橫向排列，欄位命名為 `top1` ~ `top5`。

4. **缺失值處理**
   - 使用 `bfill`（向後填補）補齊空值。
   - 若仍為空，預設以 `top1` 值填補。
   - 建立欄位列表進行進一步填補，強化資料完整性。

5. **輸出結果**
   最終輸出為 `output.csv`，可用於後續模型訓練或分析。

---
## 📁 資料集

👉 [點此前往雲端資料集](https://drive.google.com/drive/folders/15_SoKLusux3w5Xb05spBpsyOcZ1geguq?usp=sharing)

## 📁 範例輸出格式

| session_id | top1    | top2    | top3    | top4    | top5    |
|------------|---------|---------|---------|---------|---------|
| A001       | song_12 | song_03 | song_08 | song_03 | song_03 |
| A002       | song_05 | song_06 | song_01 | song_05 | song_05 |

---

## 🛠 使用技術

- Python 3
- pandas

---
