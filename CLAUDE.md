# task-board

タスク管理ボードアプリケーションのプロジェクトです。

## Git 運用ルール

### コード変更のたびに GitHub へプッシュする

ファイルを編集・追加・削除するたびに、以下の手順を必ず実行してください。

1. 変更内容を確認する
   ```
   git status
   git diff
   ```
2. 変更をステージングする（機密ファイルは除外すること）
   ```
   git add <変更したファイル>
   ```
3. コミットを作成する（コミットメッセージは変更の "なぜ" を中心に書く）
   ```
   git commit -m "コミットメッセージ"
   ```
4. GitHub へプッシュする
   ```
   git push origin <ブランチ名>
   ```

### コミットメッセージの規則

- 英語または日本語、どちらでも可
- 先頭に変更の種類を付ける：`feat:` `fix:` `refactor:` `docs:` `test:` `chore:`
- 1行目は 72 文字以内
- 変更の "what" ではなく "why" を説明する

### ブランチ戦略

- `main` ブランチは常にデプロイ可能な状態を保つ
- 機能追加・バグ修正は feature ブランチを切って作業する
- `main` への直接プッシュは禁止（PR を経由すること）

### 禁止事項

- `.env` や認証情報を含むファイルをコミットしない
- `git push --force` は明示的に許可された場合のみ
- `--no-verify` でフックをスキップしない

## デプロイ先

https://yoshikazuk009yk-cmyk.github.io/task-board/

- `main` ブランチへのプッシュで GitHub Actions が自動ビルド・デプロイする
- デプロイを手動で実行する場合は Actions タブの `Deploy to GitHub Pages` から `Run workflow` を使う

## 技術スタック

| 用途 | 技術 |
|---|---|
| UI ライブラリ | React 18 |
| ビルドツール | Vite 6 |
| 言語 | JavaScript (JSX) |
| スタイリング | CSS Modules（`App.css` / `index.css`） |
| 状態管理 | `useState` / `useEffect`（React 組み込み） |
| 永続化 | `localStorage` |
| CI/CD | GitHub Actions |
| ホスティング | GitHub Pages |

## コンポーネント命名規約

- コンポーネント名は **PascalCase**（例: `App`, `TaskItem`）
- ファイル名はコンポーネント名と一致させ **`.jsx`** 拡張子を使う（例: `App.jsx`）
- CSS ファイルはコンポーネントファイルと同名にする（例: `App.jsx` → `App.css`）
- クラス名は **kebab-case**（例: `task-item`, `add-button`, `input-row`）
- ローカルストレージのキーは `task-board-` プレフィックスを付ける（例: `task-board-tasks`）

## 開発ガイドライン

- セキュリティ脆弱性（XSS、SQL インジェクション等）を導入しない
- コメントは "なぜ" が自明でない場合にのみ記述する
- 不要な抽象化・機能追加は行わない（タスクの範囲内で実装する）
- UI 変更後は実際にブラウザで動作確認してから完了とする
