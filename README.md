# blog

`tksds.dev`で公開する技術ブログ。

記事は `src/content/posts/`にmdで置く。
Astroでビルドし、Cloudflare WorkersのStatic Assetsとして配信する。

`wrangler deploy`のたびにTerraform 管理下のrouteを上書きしにいくため、`wrangler.jsonc`には`routes`を書かかない。

## 開発

```sh
npm install
npm run dev
npm run build
```

## デプロイ

`master`へのpushでGitHub Actionsが`wrangler deploy`する。
必要なsecretは`CLOUDFLARE_API_TOKEN`(アカウント:Workers スクリプト:編集)と`CLOUDFLARE_ACCOUNT_ID`。

```sh
npx wrangler deploy
```

`workers_dev`がfalseなので公開URLは無い。
この時点で見た目を確認したければ一時的にtrueにして`<name>.<subdomain>.workers.dev`を見て、確認後falseに戻す。
