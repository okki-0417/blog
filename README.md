# blog

mumumu の個人ブログ。Astro + Markdown。

## ローカル開発

```sh
pnpm install
cp .env.example .env  # GitHub / Qiita ハンドルを記入
pnpm dev      # http://localhost:4321
pnpm build    # ./dist/ に出力
pnpm preview  # ビルド結果をローカル確認
```

## 環境変数

- `PUBLIC_GITHUB_HANDLE` — フッターの GitHub リンクに使う
- `PUBLIC_QIITA_HANDLE` — フッターの Qiita リンクに使う

未設定なら該当リンクは非表示。Cloudflare Pages では Settings → Environment variables で同じキーを登録する。

## 記事を書く

`src/content/blog/` に `.md` または `.mdx` を追加するだけ。フロントマター例:

```md
---
title: '記事タイトル'
description: '概要'
pubDate: 'Jun 02 2026'
heroImage: '../../assets/blog-placeholder-1.jpg'
---

本文を Markdown で書く。
```

## デプロイ（Cloudflare Pages）

1. GitHub に push
2. Cloudflare ダッシュボード → Workers & Pages → Create → Pages → Connect to Git
3. ビルド設定:
   - Framework preset: `Astro`
   - Build command: `pnpm build`
   - Build output: `dist`
   - 環境変数: `NODE_VERSION=22`
   - パッケージマネージャは `pnpm-lock.yaml` で自動検出される
4. Save and Deploy

以降は push するだけで自動デプロイ。

## デプロイ（Vercel に変える場合）

`vercel` CLI もしくはダッシュボードでリポジトリ連携。フレームワーク自動検出で `Astro` を選べば OK。
