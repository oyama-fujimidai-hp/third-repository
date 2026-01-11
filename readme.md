# Renamer Pro - 訪問看護報告書ファイル名自動生成ツール

Renamer Pro は、訪問看護報告書の PDF ファイルから必要な情報（日付、利用者名、医師名、管理者名）を解析し、標準化されたファイル名を自動生成するウェブアプリケーションです。

## 主な機能

- **PDF 解析**: PDF.js を使用してブラウザ上で PDF テキストを抽出。
- **ハイブリッド解析アルゴリズム**:
  - **AI 解析 (Gemini API)**: Google Gemini API (Gemini 3 Flash Preview / Pro Preview) を使用して、複雑なレイアウトの文書からも高精度に情報を抽出します。
  - **正規表現解析**: API キーがない場合や補助的な手段として、パターンマッチングによる抽出も行います。
- **手書き書類対応モード**: 
  - OCR が困難な手書き書類などの場合、特定の医師名（大西康則）や管理者名（おおぞら）を一括設定できる「手書きモード」を搭載。スイッチをオンにすることで、解析不能な項目を自動的に補完します。
- **重複チェック**: 生成されたファイル名が重複している場合に警告を表示。
- **スプレッドシート連携**: 解析結果をタブ区切り形式でクリップボードにコピーし、Google スプレッドシート等へ簡単に貼り付け可能。
- **プライバシー配慮**: 解析処理はブラウザ内で行われ、PDF ファイル自体が外部サーバーに保存されることはありません（Gemini API 使用時はテキストデータのみ送信されます）。

## 技術スタック

- **Frontend**: React (CDN 版), Tailwind CSS
- **Library**: PDF.js, Lucide Icons
- **AI**: Google Gemini API
- **Deployment**: Docker (Nginx), Cloud Run 等に対応

## 使い方

1. `src/index.html` をブラウザで開くか、Docker コンテナを起動します。
2. 必要に応じて「設定」から Gemini API キーを入力し、使用する AI モデル（Gemini 3 Flash Preview / Pro Preview）を選択します。
3. 解析したい PDF ファイルをドラッグ＆ドロップします。
4. 解析結果を確認・修正し、「スプレッドシートへ」ボタンでデータをコピーします。

## 開発・実行

### Docker での実行

```bash
docker build -t renamer-pro .
docker run -p 8080:8080 renamer-pro
```

ブラウザで `http://localhost:8080` にアクセスしてください。

---
Created for medical and nursing care professionals.
