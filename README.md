# Calendar 📚

小朋友溫書用日曆 App（Grid 介面 + 每日 AM/PM checklist）。

## 功能
- 月曆格仔介面（每格一日）
- 每日分 AM / PM checklist
- 可新增待辦、可剔選完成
- 自動儲存（localStorage）

## 使用
直接打開 `index.html` 即可使用。

## Security & Deployment

為了保護您的 Firebase 專案，請務必執行以下設定：

### 1. 限制 API Key (Google Cloud Console)
由於 API Key 會暴露在前端程式碼中，請前往 Google Cloud Console 限制其使用範圍：

1. 進入 [Google Cloud Console > API & Services > Credentials](https://console.cloud.google.com/apis/credentials)。
2. 找到您的 Firebase API Key (通常命名為 `Browser key` 或 `Auto created by Firebase`)。
3. 點擊編輯，設定 **Application restrictions**：
   - 選擇 **HTTP referrers (web sites)**。
   - 新增您的網域 (例如：`https://your-app.vercel.app/*` 或 `http://localhost:3000/*` 進行開發測試)。
4. (選用) 設定 **API restrictions**：
   - 選擇 **Restrict key**。
   - 只勾選需要的 API (例如：`Cloud Firestore API`, `Firebase Authentication API`)。

### 2. 設定 Firestore 安全規則
專案中已包含 `firestore.rules` 檔案，限制只有登入的使用者才能讀寫資料。

請安裝 Firebase CLI 並部署規則：

```bash
# 安裝 Firebase CLI
npm install -g firebase-tools

# 登入 Firebase
firebase login

# 初始化 (如果尚未初始化)
firebase init firestore

# 部署規則
firebase deploy --only firestore:rules
```
