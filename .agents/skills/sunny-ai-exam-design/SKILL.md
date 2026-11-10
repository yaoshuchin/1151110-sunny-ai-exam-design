---
name: sunny-ai-exam-design
description: >-
  佳釧老師（Sunny 老師）溫潤手作手帳風 × AI 協作考卷與教育評量工作台的網頁風格編排與前端設計技能。
  當需要建構素養導向命題、教材拆解、教學研習成果、教案展示、試卷對齊、互動提示詞工作室（Prompt Studio）、
  手帳風圖卡排版、磨砂玻璃門禁密碼鎖（Password Gate nato）或線上劃記螢光筆工具時使用。
---

# 佳釧老師風格：溫潤手作手帳風 × AI 協作考卷與評量工作台設計規範

本技能完整封裝 **佳釧老師（Sunny 老師）「如何運用 AI 設計考卷大解密」** 之視覺風格體系、版面編排哲學、色彩系統、手作質感細節、試卷深度拆解排版與互動工作台元件庫。

---

## 🎨 一、風格哲學與視覺識別系統 (Visual Identity)

### 1. 核心意象：溫潤紙感 × 手帳文集 × 專業教學對齊
- **紙張溫潤感 (Warm Paper Aesthetic)**：避免冷冽的純白與高對比黑，以米黃、奶油白與沉穩墨灰構建如手寫講義般的舒適閱讀感受。
- **莫蘭迪粉彩點綴 (Morandi Pastel Accents)**：以灰紫（Lavender）、薄荷水綠（Mint）、蜜桃粉杏（Peach）進行模組分類，低飽和度但層次分明。
- **手作細節 (Handmade Craft Details)**：標楷體大字標題、手繪螢光劃記底線、手帳打孔線（Binding Holes）、紙膠帶貼角（Washi Tape）與手壓印章徽章。

### 2. CSS 核心變數 (Theme Tokens)

```css
:root {
  /* 基底與紙張 */
  --bg: #fbf8f1;         /* 暖米底色 */
  --paper: #fffefa;      /* 精緻紙張白 */
  --ink: #3f4142;        /* 沉穩墨灰（非純黑） */
  --muted: #73746f;      /* 說明文字灰 */
  --line: #e4ded3;       /* 柔和分隔線 */

  /* 核心主色 */
  --purple: #736889;     /* 莫蘭迪紫灰（品牌主色） */
  --purple-dark: #5b526c;/* 按鈕深度下陰影 */

  /* 莫蘭迪粉彩情境色 */
  --lavender: #eceaf0;   /* 薰衣草灰紫 */
  --mint: #e6efe7;       /* 薄荷柔綠 */
  --peach: #f7e7db;      /* 蜜桃粉杏 */
  --yellow: #f4e6b8;     /* 奶油柔黃（高光筆刷色） */

  /* 幾何規範 */
  --radius: 20px;
  --radius-lg: 24px;
}
```

### 3. 字體與排版規範 (Typography)

```css
/* 全局字體設定 */
body {
  margin: 0;
  color: var(--ink);
  background: var(--bg);
  font: 16px/1.8 "Microsoft JhengHei", "PingFang TC", -apple-system, sans-serif;
  letter-spacing: 0.025em;
}

/* 主標題採用標楷體/楷書，營造人文教育感 */
.hero h1, .page-heading h1, .notebook h2 {
  font-family: "DFKai-SB", "BiauKai", "Microsoft JhengHei", serif;
  font-size: clamp(38px, 4.5vw, 57px);
  font-weight: 600;
  line-height: 1.45;
  letter-spacing: 0.06em;
}

/* 標題中的重點詞 (em) 著品牌紫色，不斜體 */
em {
  color: var(--purple);
  font-style: normal;
}

/* 螢光筆劃記標記效果 (Underline Marker) */
.underline {
  position: relative;
  z-index: 1;
  white-space: nowrap;
}
.underline:after {
  content: "";
  position: absolute;
  background: #efdfad;
  height: 13px;
  bottom: 2px;
  left: 0;
  right: 0;
  z-index: -1;
  transform: rotate(-2deg);
  border-radius: 40%;
}
```

---

## ✂️ 二、手作質感特徵元件 (Craft Components)

### 1. 手帳筆記卡（含打孔裝訂線）
```css
.notebook {
  background: var(--paper);
  border: 1px solid #dcd6ca;
  border-radius: 4px 18px 18px 4px;
  transform: rotate(3deg);
  padding: 33px 30px 16px 43px;
  box-shadow: 8px 9px 0 #eae3d750, 0 15px 30px #776e5010;
  position: relative;
}

/* 模擬活頁裝訂打孔線 */
.notebook:before {
  content: "";
  position: absolute;
  left: 15px;
  top: 12px;
  bottom: 12px;
  width: 10px;
  background: radial-gradient(ellipse, #c5bba8 3px, transparent 4px) 0 0/10px 24px repeat-y;
}
```

### 2. 紙膠帶貼紙 (Washi Tape)
```css
.tape {
  position: absolute;
  z-index: 2;
  background: #d5d0dda8;
  height: 28px;
  width: 100px;
  transform: rotate(-12deg);
  top: 4px;
  left: 43%;
  clip-path: polygon(0 0, 100% 4%, 96% 100%, 3% 96%);
}
```

### 3. 不對稱手蓋印章標誌 (Brand Stamp)
```css
.brand-icon {
  border: 1.6px solid var(--purple);
  border-radius: 50% 46% 48% 42%;
  width: 44px;
  height: 44px;
  display: grid;
  place-items: center;
  color: var(--purple);
  font: 25px "DFKai-SB", serif;
  transform: rotate(-8deg);
  background: var(--lavender);
}
```

---

## 📐 三、六大版面編排模組 (Layout Modules)

### 模組 1：Hero 雙欄不對稱首頁
- **左欄（概念與動機）**：
  - 小眉標（`eyebrow`，如：`佳釧老師 · 研習講義精華`）
  - 楷體大標題（含 `<em>` 與 `.underline`）
  - 素養理念導言（`hero-intro`）
  - 立體感按鈕組（`.primary` 實心紫底深陰影、`.secondary` 邊框感）
- **右欄（視覺展示）**：
  - 微傾斜的手帳卡片，內含打孔線、紙膠帶、SVG 手繪幾何圖與小標註。

### 模組 2：三欄素養理念圖卡 (`.principles`)
```html
<section class="principles">
  <article class="principle lavender">
    <div class="principle-icon">🎯</div>
    <h3>先對準能力</h3>
    <p>先確認想檢測孩子什麼素養或歷程，再決定文本長相與題型難度。</p>
  </article>
  <article class="principle mint">
    <div class="principle-icon">📖</div>
    <h3>用文本承載思考</h3>
    <p>好的文本讓學生不僅是檢索訊息，更能進行深度推論與意義整合。</p>
  </article>
  <article class="principle peach">
    <div class="principle-icon">🔍</div>
    <h3>從答案看見理解</h3>
    <p>選項誘答要具診斷性，能精準洞察出學生的常見迷思概念。</p>
  </article>
</section>
```

### 模組 3：命題設計思維 5 步驟標籤頁 (`.process-tabs`)
- **五步驟標籤列**：
  `01 確認考點` ➔ `02 確認評量架構` ➔ `03 選擇題材` ➔ `04 設計題目` ➔ `05 檢核修改`
- **雙欄對照結構**：
  - 左欄：**教師專業把關**（學科本質、雙向細目表、年級適用性）
  - 右欄：**AI 協作助手**（生成情境文本、設計高診斷性誘答、編寫多版本題目）
- **提示詞（Prompt）展示卡**：淺灰白背景、虛線邊框、一鍵複製按鈕。

### 模組 4：試卷深度拆解與誘答分析（雙欄式案例研究）
- **左欄（真實試卷切片視圖）**：
  - 固定比例（`aspect-ratio: 210/297` 或 `22/17`），支援點擊展開大圖燈箱（Modal）。
  - 附上原題掃描檔與 PDF 下載卡片（`download-card`）。
- **右欄（命題深度解構）**：
  - 學習表現與學習內容指標代碼
  - 認知歷程向度（提取／推論／詮釋／評估）
  - 誘答設計心理學（分析 A、B、C、D 各選項的迷思設計）
  - 評分規準與教學回饋引導

### 模組 5：PIRLS 閱讀歷程認知階梯 (`.ability-parallel`)
四個階梯橫向或直向漸進：
1. **直接提取（Retrieve）**：在文本中直接找到明確陳述的訊息。
2. **直接推論（Inference）**：連結前後文、推導因果關聯或代名詞指涉。
3. **詮釋、整合（Interpret & Integrate）**：歸納主旨、梳理結構、理解全文意涵。
4. **比較、評估（Evaluate）**：批判檢視論點、評價寫作手法或發表個人觀點。

### 模組 6：避開命題地雷網格 (`.mine-grid`)
- 醒目的警示標籤（如：`地雷 01：字面搜尋題過多`、`地雷 02：語病與洩漏答案`）
- **修改前 vs 修改後** 左右對照卡片，清晰標示出問題盲點與改善解方。

---

## 🛠️ 四、互動工作台與外掛工具 (Interactive Tooling)

### 1. 磨砂玻璃門禁密碼系統 (`#passwordGate`)
適用於研習、校內工作坊或專屬教材，預設通行密碼 `nato`：
- **視覺**：高質感全螢幕毛玻璃背景（`backdrop-filter: blur(14px)`），中央柔白卡片。
- **機制**：
  - 支援大小寫與前後空白修剪 (`.trim().toLowerCase() === 'nato'`)。
  - 登入狀態存入 `localStorage`，重新整理不重複詢問。
  - 支援 URL 快速通關參數：`?pw=nato`。
  - 右下角常駐浮動按鈕：`🔒 鎖定網站`，隨時可一鍵鎖定以利展示或交替測試。

### 2. 懸浮劃記螢光筆與橡皮擦 (`#markTools`)
專為線上報告、投影講解與讀卷研習設計：
- 懸浮可拖曳面板（Highlight 模式、Eraser 模式、筆刷粗細切換、清除全部）。
- 全螢幕透明 `<canvas>` 覆蓋層，支援視窗捲動座標校準與手勢觸控繪圖。

### 3. AI 出題工作室 (Prompt Studio)
- 互動式選項產生器：下拉點選「年級」、「文體類型」、「評量向度」、「題型（單選／多選／問答／短文）」。
- 即時動態拼接「AI 命題指令（Prompt）」。
- 懸浮 Toast 提示：點擊「複製提示詞」後彈出 3.2 秒自動淡出的成功提示框。

---

## 🚀 五、實作範本快速啟動 (Starter Template)

建立標準佳釧老師風格單頁網站的基礎骨架：

```html
<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>單元名稱｜佳釧老師</title>
  <style>
    :root {
      --bg: #fbf8f1;
      --paper: #fffefa;
      --ink: #3f4142;
      --muted: #73746f;
      --purple: #736889;
      --line: #e4ded3;
      --lavender: #eceaf0;
      --mint: #e6efe7;
      --peach: #f7e7db;
      --yellow: #f4e6b8;
    }
    body { margin: 0; background: var(--bg); color: var(--ink); font-family: "Microsoft JhengHei", sans-serif; line-height: 1.8; }
    header { max-width: 1200px; margin: auto; padding: 24px; display: flex; justify-content: space-between; align-items: center; }
    .brand { font-weight: 700; font-size: 18px; color: var(--ink); text-decoration: none; }
    nav { position: sticky; top: 0; background: rgba(251, 248, 241, 0.95); backdrop-filter: blur(10px); border-block: 1px solid var(--line); display: flex; justify-content: center; z-index: 100; }
    nav a { padding: 14px 22px; color: var(--muted); text-decoration: none; font-size: 15px; }
    nav a.active { color: var(--purple); font-weight: 700; border-bottom: 3px solid var(--purple); }
    main { max-width: 1160px; margin: auto; padding: 40px 24px; }
  </style>
</head>
<body>
  <header>
    <a class="brand" href="#">佳釧老師 · AI 協作考卷評量工作台</a>
  </header>
  <nav>
    <a href="#home" class="active">01 語文評量重點</a>
    <a href="#alignment">02 教什麼，考什麼</a>
    <a href="#assessment">03 評量向度探索</a>
    <a href="#studio">04 AI 出題工作室</a>
  </nav>
  <main>
    <!-- 依據六大模組自由編排 -->
  </main>
</body>
</html>
```

---

## 📌 六、檢核清單 (Quality Checklist)

在產出或修改此風格網頁時，依序檢核：
1. [ ] **配色是否溫潤舒適**：確認基底為 `#fbf8f1`，沒有刺眼的純白背景或純黑字。
2. [ ] **標題是否具手作感**：主標題是否套用楷體系列字體並搭配 `.underline` 螢光筆劃記。
3. [ ] **教學理念與 AI 是否對齊**：是否呈現「教師把關素養向度，AI 負責生成與誘答深化」的協作架構。
4. [ ] **試卷案例是否有深度解析**：是否清晰標明認知層級（PIRLS 4 層次）與迷思誘答心理分析。
5. [ ] **門禁保護與複製功能**：密碼保護（`nato`）、提示詞一鍵複製與 Toast 回饋是否運作順暢。
