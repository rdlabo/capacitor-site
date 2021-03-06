---
title: Capacitor Web Documentation
description: Web Getting Started
url: /docs/web
contributors:
  - mlynch
---

# WebプロジェクトでのCapacitorの利用

<p class="intro">Capacitor従来のWebアプリケーションとProgressive Web Appsを完全にサポートします。実際、Capacitorを使えば、iOSとAndroidのアプリストアアプリのPWAバージョンを最小限の作業で簡単にリリースできます。</p>

### インストール

Chances are, you already have Capacitor installed in your app if you're using Capacitor to build an iOS, or Android app. In capacitor, the `web` platform is just the web project that powers your app!

If you don't have Capacitor installed yet, consult the [Installation](/docs/getting-started/) guide before continuing.

#### CapacitorをModuleとして使う

一般的に、アプリをつくる時には、JavaScriptモジュールのインポートをサポートするビルドシステムを備えたフレームワークを使用します。
その場合は、アプリの上部に Capacitor をインポートすればOKです:

```typescript
import { Capacitor } from '@capacitor/core';
```

プラグインを使用するには、 `プラグイン` をインポートして呼び出します。
実際に便利な機能を提供するのは、Webサポート付きのプラグインだけです。

```typescript
import { Plugins } from '@capacitor/core';

const position = await Plugins.Geolocation.getCurrentPosition();
```

### ScriptタグからCapacitorを利用する

ビルドシステムまたはバンドラー/モジュールローダーを使用していない
WebアプリケーションでCapacitorコアを使用するには、`capacitor.config.json` で `bundledWebRuntime` を `true` に設定し、
指定したバージョンのCapacitor CoreをプロジェクトにコピーするようにCapacitorに指示してから、
`index.html`に`capacitor.js` をインポートする必要があります:

```json
{
  "bundledWebRuntime": true
}
```

プロジェクトにコピーしてください。

```bash
npx cap copy web
```

`index.html`で、`capacitor.js`をあなたのアプリのJSの前に読み込みます:

```html
<script src="capacitor.js"></script>
<script src="your/app.js"></script>
```

## アプリの開発

あなたは[Ionic](http://ionicframework.com/)のようなUIコンポーネントとビルドシステムを採用してるかもしれません。 
その場合、Capacitorアプリでも、そのフレームワークのものを使ってください！

フレームワークを使用していない場合、CapacitorにはHTML5ルーティングをサポートする小さな開発サービスが付属しています。
これを使用するには、以下を実行してください:

```bash
npx cap serve
```

## 本番に反映する

Progressive Web Appを公開して、世界と共有する準備ができたら、Webディレクトリのコンテンツをアップロードします
(例えば `www/` や `build/` フォルダです)。

これには、アプリケーションを実行するために必要なものがすべて含まれています！
