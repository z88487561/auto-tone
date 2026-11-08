# 批次自動調色

在瀏覽器中分析、調整並批次匯出照片的免安裝工具。照片只在本機瀏覽器處理，不會上傳到伺服器。

## 功能

- 一次載入多張照片，依瀏覽器支援度接受 JPG、PNG、WebP、HEIC 等格式。
- 自動分析照片並提供曝光、對比、亮部、陰影、白色、黑色、鮮豔度及飽和度調整。
- 可預覽調整結果、比較原圖，並微調單張照片。
- 匯出 JPEG、WebP 或 PNG；可設定品質與長邊尺寸。
- 批次處理多張照片時下載 ZIP。
- 支援安裝為 PWA；首次連線載入後可離線開啟應用程式。

## 使用方式

1. 在支援現代 JavaScript 與 Canvas API 的瀏覽器開啟網站。
2. 點選上傳區或拖曳照片進入。
3. 調整自動強度、單張參數與輸出設定。
4. 按「處理全部並下載」或「只下載這張」。

選取照片及輸出皆在瀏覽器本機完成；請使用可信任的裝置處理私人照片。

## 本機執行

PWA 與 Service Worker 需要安全來源；本機開發請使用 `localhost`，不要直接以 `file://` 開啟。

例如使用 Python 啟動簡易靜態伺服器：

```bash
python -m http.server 8000
```

接著開啟 <http://localhost:8000>。

## 部署到 GitHub Pages

1. 將專案檔案推送到 GitHub repository 的 `main` 分支。
2. 在 repository 開啟 **Settings → Pages**。
3. 在 **Build and deployment** 選擇 **Deploy from a branch**，分支選 `main`，資料夾選 `/(root)`，再按 **Save**。
4. 等待部署完成，使用 Pages 顯示的 HTTPS 網址開啟網站。

專案使用相對路徑，可部署在 GitHub Pages 的 repository 子路徑下。首次開啟時需連線下載離線資源；更新部署後，Service Worker 會以新版快取取代舊版。

## 專案檔案

| 檔案 | 用途 |
| --- | --- |
| `index.html` | 應用程式、介面與影像處理程式 |
| `manifest.webmanifest` | PWA 名稱、啟動方式及圖示設定 |
| `sw.js` | 離線快取與 Service Worker |
| `icon.svg`、`icons/` | 網站及安裝圖示 |

本專案沒有外部執行期相依套件。
