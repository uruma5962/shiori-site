# 公開ページのセットアップ手順

このフォルダ (`docs/`) には、App Store 申請に必要なプライバシーポリシー (`privacy.md`) とサポート (`support.md`) の公開ページが入っています。

## GitHub Pages で公開する手順

### 方法 A: 新規リポジトリを作る (シンプル)

1. GitHub で **`shiori-site`** などの新しい公開リポジトリを作る (Private でも OK だが、Pages を使うには公開アカウント設定が必要)
2. このフォルダの `index.md` `privacy.md` `support.md` をリポジトリ直下に push
3. GitHub のリポジトリ Settings → **Pages**
4. Source: **Deploy from a branch**
5. Branch: **main** / Folder: **/ (root)**
6. Save → 数分待つ
7. URL は `https://<ユーザー名>.github.io/<リポジトリ名>/` の形になる
8. アプリの `app/about.tsx` の 17-19 行目を実際の URL に書き換え:

```ts
const PRIVACY_POLICY_URL = 'https://<ユーザー名>.github.io/<リポジトリ名>/privacy';
const SUPPORT_URL = 'https://<ユーザー名>.github.io/<リポジトリ名>/support';
```

### 方法 B: 既存リポジトリの docs/ を使う

しおりアプリ本体のリポジトリで `docs/` フォルダを Pages として公開する手もあります。

1. リポジトリ Settings → Pages
2. Source: **Deploy from a branch**
3. Branch: **main** / Folder: **/docs**
4. Save

これで `https://<ユーザー名>.github.io/<リポジトリ名>/privacy` でアクセスできるようになります。

## カスタムドメインを使う場合 (任意)

独自ドメインを持っているなら、Pages の設定で「Custom domain」を指定できます。`shiori.example.com` のようなアドレスで公開可能。

## Notion の公開ページで代替する場合

GitHub Pages を使いたくない場合は Notion のページを公開して URL を使うこともできます。Apple の審査も Notion ページの URL で問題なく通ります。

1. Notion で「Privacy Policy」「Support」のページを作る
2. `privacy.md` / `support.md` の内容を貼り付け
3. 右上「共有」→ 「Web で公開」→ 公開 URL をコピー
4. `app/about.tsx` の URL を差し替え

## App Store Connect 側の設定

リリース時にも以下を設定します。

- App Store Connect → アプリ → **App 情報**
  - プライバシーポリシー URL: `https://.../privacy`
  - サポート URL: `https://.../support`
- App Privacy 質問: 「データを収集しますか?」 → **No**

## 連絡先メール

`uruma5962@gmail.com` が `privacy.md` `support.md` `app/about.tsx` の 3 箇所に書かれています。
変更したい場合は 3 箇所すべて書き換えてください。
