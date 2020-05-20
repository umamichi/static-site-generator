# 静的サイトジェネレーター Gatsby

## 静的サイトジェネレーターとは？

Static Site Generator（SSG）

WebサイトのHTMLファイルを生成するツールのこと

Wordpressのような従来CMSの仕組みは、MySQLなどのDBをもとに、サーバーでHTMLを生成して返すものだった

<img src="https://user-images.githubusercontent.com/7469495/77660631-ec775600-6fbc-11ea-954f-46f16c1c1fcf.png">


それに対し静的サイトジェネレーターは、コンパイル時にGraphQLやAPIからすべてのデータを取得し全てのHTMLを最初に生成する

さらに、生成されたファイルを、Netlifyなどのホスティングサービスを用いて、サーバーレスで公開する仕組みが主流になっている


<img src="https://github.com/umamichi/static-site-generator/raw/master/2.png">

## 静的サイトジェネレーターのメリット

※ Netlifyなどホスティングサービスを用いた場合

+ レスポンスが速い。サーバーでHTMLを動的に生成しないから

+ サーバー代 ¥0✨ サーバーが必要ないため 

+ サーバー落ちない。メンテが不要

	※ ただしホスティングサービスが落ちる可能性はあります


+ headless CMS と相性が良い

	headless CMS・・・HTMLなどビュー機能がないCMS。コンテンツを管理する仕組みのみを持ち、APIのみ提供する


+ LPやブログなどに相性が良い


## デメリット

+ 膨大なページ量のWebサイトには向かない

+ ビルドの時間がかかる。ページ数が多くなるほど遅くなる

+ 頻繁にデータ更新があるサイトに向かない

	データの更新のたびにビルドを走らせる必要があるため

+ API頻繁にリクエストするサイトには向かない


## 有名な静的サイトジェネレーター

400を超える数がある

<img src="https://github.com/umamichi/static-site-generator/raw/master/1.png">

過去2年で、フレームワークが成熟したらしく、代表的なものは以下↓

+ **Gatsby**

	これが一番有名、欧米で流行っている。

	React.js、Webpack、GraphQL、CSSなどで SPA を作成するのに最適
	
    Headless CMS、SaaSサービス、API、データベースなどに対応
    
+ Next, Nuxt

	Gatsbyが登場する前は、Next, Nuxt が主流だった

+ Hugo

+ Jekyll

2020年3月現在、[静的ジェネレータ人気順が見れるサイト](https://www.staticgen.com/) によると、Javascript 言語では Gatsby と Next.js が人気

<img src="https://user-images.githubusercontent.com/7469495/77657541-cd76c500-6fb8-11ea-8649-6da0442c765f.png">

## Gatsbyの特徴

<img src="https://user-images.githubusercontent.com/7469495/77665287-cc4a9580-6fc2-11ea-9564-434ac4f13db5.png">


+ Reactベース

+ GraphQLと相性良い

+ Gatsby, Inc.(2015年設立）が開発、シリコンバレーにある

+ IBM、PayPal、Braun、Airbnb などが利用

静的サイトジェネレータは、もともとNextやNuxtのアイデンティティでしたが

Gatsbyの登場により静的サイトジェネレータは別にNextやNuxtじゃなくてもいいのでは？という風潮になってきた

+ Gatsbyプラグインが多数、npmで公開されていて以下のようなことができる

	TypeScript化, PWA対応, WordPress連携, Contentful連携,GA組み込み などなど [その他はこちら参考](https://qiita.com/Takumon/items/da8347f81a9f021b637f)


## Jamstack（ジャムスタック）と Lampstack（ランプスタック）

Gatsbyに代表されるようなモダンなウェブサイトの仕組みのことを指すワードがここ1〜2年で注目されてきた

対義語としてLampstackがある

### Jamstack

**J** ・・・ JavaScript

**a** ・・・ API

**m** ・・・ Markup

Webサーバーに依存しない、つまり**サーバーレス**であるウェブサイトのことをJamstackであると言える

### Lampstack

**L** ・・・ Linux

**a** ・・・ Apache, Webサーバ

**m** ・・・ MariaDB・MySQL

**p** ・・・ PHP・Perl・Python

WordPress のようなサーバーサイドとクライアントサイドが**密結合**なウェブサイトをLampstackであると言える


## Create React App, Nuxt (Next), Gatsby の使い分け

### Create React App

すべてCSR（クライアントサイドレンダリング）SEOを捨てることになる

ブラウザベースのWEBアプリケーションに向いている

APIのレスポンスを待ってDOM描画するため、描画まで待ち時間が発生する

コーポレートサイトやLPには不向き

### Nuxt (Next)

APIのレスポンス結果も含めてSSRするのでSEOは完璧。

データ更新が多い（APIレスポンスが頻繁に変わる）サイトに向いている

### Gatsby

ビルド時点で静的なHTMLを生成する。SEOは完璧。描画や遷移が爆速。

ただし、頻繁なデータ更新には向かない。都度ビルドとデプロイが必要。



| | Create React App | Nuxt | Gatsby |
| --- | --- | --- | --- |
| SEO | × | ◯ | ◯ |
| 頻繁なデータ更新 | ◯ | ◎ | △ |
| 描画速度 | △ | ◯ | ◯ |
| LP | × | ◯ | ◯ |
| CMS系（e.g. ブログ, コーポレートサイト） | △ | ◯ | ◎ |
| WEBアプリ（e.g. TODOアプリ） | ◯ | ◯ | × |
| 大規模Webサービス | × | ◎ | × |
| サーバーコスト・メンテナンス | ◯ | × | ◎ |



## Gatsbyを試したサンプル

自分の環境で試したい方は

公式ドキュメントのクイックスタートで簡単に試すことができます

https://www.gatsbyjs.org/docs/quick-start/

`gatsby-cli` をインストールし、開発環境を作るとあらかじめディレクトリ、ファイルなどが用意されます

以下コマンドで開発環境を起動します

```sh
$ gatsby develop
```


## 少し触ってみたサンプル

### 遷移には `<Link></Link>` を使う

pjaxのような挙動をする

カーソルをリンク先に乗せた瞬間に、遷移先のhtmlをprefetchし、DOM書き換えとpushStateにより遷移

これにより爆速で遷移される

<img src="https://user-images.githubusercontent.com/7469495/77927562-55730c80-72e2-11ea-97e8-f44e4f1e73e5.png">


### GraphQLを試す

起動後

`http://localhost:8000/___graphql` にアクセスすると、GraphQL Explorerが使える

<img src="https://user-images.githubusercontent.com/7469495/77926378-04aee400-72e1-11ea-9ad5-786fed197e39.png">


[GitHub GraphQL API](https://developer.github.com/v4/explorer/) と同様、ここでGraphQLにより取得できるデータを試すことができる


### GraphQL を用いて.md からデータを取得する

[gatsby-source-filesystem](https://www.npmjs.com/package/gatsby-source-filesystem) というプラグインを使い、ローカルファイルを取得することができる

さらに、[gatsby-transformer-remark](https://www.npmjs.com/package/gatsby-transformer-remark) でマークダウンファイルを解析する。HTML形式へ変換して取得も可能。

```sh
$ yarn add gatsby-source-filesystem gatsby-transformer-remark
```

gatsby-config.js に以下を追記

```javascript
    // ローカルファイルのデータをGatsbyに渡せるプラグイン
    {
      resolve: "gatsby-source-filesystem",
      options: {
        path: `${__dirname}/blog`,
        name: "blog",
      },
    },
```

`/blog` 以下のファイルをgraphQLで取得できるようになる

`/blog/hello-world.md` を追加

```markdown
---
title: Hello World this is title.
date: "2020-04-01"
categories: []
---

これは、hello-world.md の本文です。

**太字**

## 見出し

Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。

Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。Hello World。
```

さらに、`/pages/get-markdown.js` を追加

```javascript
import React from "react"
import { useStaticQuery, graphql } from "gatsby"
import Layout from "../components/layout"

const GetMarkdown = () => {
  // useStaticQuery は gatsby に用意されているメソッド
  // ビルド時にGraphQLでクエリすることができる
  // https://www.gatsbyjs.org/docs/use-static-query/#composing-custom-usestaticquery-hooks
  const data = useStaticQuery(graphql`
    query {
      allMarkdownRemark(sort: { fields: [frontmatter___date], order: DESC }) {
        totalCount
        edges {
          node {
            id
            html # 本文をHTMLに変換して取得する
            frontmatter {
              title
              date(formatString: "YYYY年MM月DD日")
            }
            excerpt # 本文抜粋
          }
        }
      }
    }
  `);

  console.log('data:', data);

  return (
    <Layout>
      <strong>投稿数 ( {data.allMarkdownRemark.totalCount} ) </strong>
      {data.allMarkdownRemark.edges.map(
        ({
          node: {
            id,
            html,
            frontmatter: { title, date },
            excerpt,
          },
        }) => (
          <div key={id}>
            <div>{date}</div>
            <h2>{title}</h2>
            {/* <p>本文抜粋：{excerpt}</p> */}
            <div dangerouslySetInnerHTML={{ __html: html }} />
          </div>
        )
      )}
    </Layout>
  )
}

export default GetMarkdown;
```


結果はこちら：https://gatsby-site-umamichi.netlify.com/get-markdown/


### Contentful からデータを取得し、DOMに反映する

こちらも、 [gatsby-source-contentful](https://www.npmjs.com/package/gatsby-source-contentful) というプラグインを用いる

```sh
$ yarn add gatsby-source-contentful
```

gatsby-config.js に以下を追記

```javascript
    // contenful からデータを取ってくるプラグイン
    {
      resolve: `gatsby-source-contentful`,
      options: {
        spaceId: '**********',
        accessToken: '**********',
      },
    },
```

`spaceId` `accessToken` はContentfulの管理画面から取得できる

今回はシンプルに以下のような`Userデータ`を作成

| name | age |
| --- | --- |
| john | 5 |
| umamichi | 27 |


`pages/contentful.js` を作成

```javascript
import React from "react"
import { useStaticQuery, graphql } from "gatsby"
import Layout from "../components/layout"

const Contentful = () => {
  const data = useStaticQuery(graphql`
    query {
      # contentful からデータを取得する
      allContentfulUser {
        edges {
          node {
            id
            age
            name
          }
        }
      }
    }
  `);

  console.log('data:', data);

  return (
    <Layout>
      {data.allContentfulUser.edges.map((
        {
          node: { id, name, age }
        }
      ) => (
        <h3 key={id}>
          {name} (age: {age})
        </h3>
      ))}
    </Layout>
  )
}

export default Contentful;
```

結果はこちら：https://gatsby-site-umamichi.netlify.com/contentful/


試したい方は、詳細な手順はこちらから。
https://qiita.com/ozaki25/items/cf7a0d9cc346e55469bc

### ビルドしてNetlifyで公開する

ビルド

```sh
$ gatsby build
```

`public` ディレクトリにこのようにファイルが生成される

<img src="https://user-images.githubusercontent.com/7469495/77933679-09c46100-72ea-11ea-93ef-e17406708027.png">

contentfulのデータなども一式組み込まれている

ちなみに、上記のサンプル含めたった4ページで初回ビルドにかかった時間は `27.9s` 

こちらはまだまだ改善の余地ありそう。というかぜひしていただきたい。

キャッシュされるようで、2回目以降のビルドは `15s` くらいに落ち着いた。

Netlifyの公開手順は省略しますが、[このあたりの記事](https://qiita.com/shozzy/items/dadea4181d6219d2d326)を参考にしてみてください。5分で公開完了👇

https://gatsby-site-umamichi.netlify.com/

## まとめ


+ Gatsbyに代表される静的サイトジェネレーターによりwebpackで環境構築するコストが削減できる

	ページ遷移の爆速化、画像の最適化圧縮なども自動で行ってくれる

+ 開発するWebサイトの特性に合わせて、フレームワーク使い分けが重要

+ WordPressなどLampstackなCMSが淘汰される

+ Gatsbyの学習コストは肌感でjQuery習得くらい（Nuxtほど大変ではない）が、山のようにあるプラグインを使いこなせるかが重要

	保守されなくなるプラグインありそうなので、プラグイン選びは慎重にすべき

+ 頻繁にAPIリクエストするような動的Webサイト以外はすべて、Gatsby採用しても良いでしょう

+ HTMLコーダーに求められるスキルが React や Vue 込みになってくる

+ 日本は世界のトレンドから1年くらい遅れる傾向があるので2020年から静的サイトジェネレータがもっと普及していくと予想（期待）



## 参考

https://cloudlance-motio.work/post/static-site-generator-blog-3/

https://ferret-plus.com/9413

https://snipcart.com/blog/choose-best-static-site-generator

https://qiita.com/uehaj/items/1b7f0a86596353587466

https://qiita.com/hppRC/items/00739eaf9ae7fc95c1ca

https://note.com/erukiti/n/na654ad7bd9bb#PArTE

https://watablogtravel.com/cra-create-react-app-next-js-gatsby%E3%80%90-%E3%81%A9%E3%81%86%E4%BD%BF%E3%81%84%E5%88%86%E3%81%91%E3%82%8B%E3%81%AE%E3%81%8B%EF%BC%9F%E3%80%91/#Nextjs

https://www.wikiwand.com/ja/LAMP_(%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2%E3%83%90%E3%83%B3%E3%83%89%E3%83%AB)

https://jp.techcrunch.com/2019/09/27/2019-09-26-gatsby-raises-15m-series-a-for-its-modern-web-development-platform/

https://qiita.com/Takumon/items/da8347f81a9f021b637f


https://qiita.com/okumurakengo/items/c34aa980afec9957a928

https://qiita.com/ozaki25/items/cf7a0d9cc346e55469bc

https://watablogtravel.com/cra-create-react-app-next-js-gatsby%E3%80%90-%E3%81%A9%E3%81%86%E4%BD%BF%E3%81%84%E5%88%86%E3%81%91%E3%82%8B%E3%81%AE%E3%81%8B%EF%BC%9F%E3%80%91/
