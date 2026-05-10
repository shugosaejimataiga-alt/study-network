

# HTTP / ネットワーク基礎 Day1

# Day1の目的

Webページを見る時、
ブラウザの裏で何が起きているかを理解する。

特に、

- HTTP通信
- URL
- request / response
- localhost
- port
- DevTools
- cache

を体感することが目的。

---

# 作成したフォルダ

```text
C:\Users\Shugo Yamasaki\Desktop\study-network
```

このフォルダは、

「通信を壊して学ぶ専用環境」

として使用する。

React/Laravelサッカーアプリとは完全分離。

---

# PowerShellで行ったこと

## フォルダ作成

```powershell
mkdir study-network
```

mkdir は：

```text
make directory
```

の略。

フォルダを作成するコマンド。

---

## フォルダ移動

```powershell
cd study-network
```

cd は：

```text
change directory
```

の略。

現在いる場所を移動する。

---

# VSCodeを開く

最初：

```powershell
code.
```

を実行してエラーになった。

理由：

```text
code.
```

を1つの文字列としてPowerShellが認識したから。

正しくは：

```powershell
code .
```

空白が必要。

意味：

```text
code   → VSCode起動
.      → 現在フォルダ
```

つまり：

```text
現在フォルダをVSCodeで開く
```

という意味。

---

# test.html 作成

study-network 内に：

```text
test.html
```

を作成。

HTMLは：

```text
HyperText Markup Language
```

の略。

ブラウザへ：

```text
どう表示するか
```

を伝えるファイル。

---

# 書いたHTML

```html
<!DOCTYPE html>
<html>
<head>
  <title>HTTP Study</title>
</head>

<body>
  <h1>Hello HTTP</h1>
</body>
</html>
```

---

# HTML理解

## h1

```html
<h1>Hello HTTP</h1>
```

意味：

```text
見出しを表示する
```

ブラウザはHTMLを解釈して画面表示する。

つまり：

```text
ブラウザ = HTMLを解釈するプログラム
```

---

# Live Server 起動

VSCode右下：

```text
Go Live
```

を押した。

表示されたURL：

```text
http://127.0.0.1:5500/test.html
```

---

# URLの理解

URL全体：

```text
http://127.0.0.1:5500/test.html
```

---

## http://

通信ルール。

HTTP通信を使用するという意味。

---

## 127.0.0.1

通信先PC。

今回は：

```text
自分自身のPC
```

を意味する。

127.0.0.1 は：

```text
localhost
```

とも呼ばれる。

---

## 5500

port番号。

意味：

```text
どのプログラムへ通信するか
```

を表す入口番号。

今回は：

```text
Live Server
```

が5500番で待ち受けしている。

---

## /test.html

欲しいファイル名。

---

# サーバーとは何か

重要：

```text
サーバー = 特別なPC
```

ではない。

本質は：

```text
通信を待ち受けするプログラム
```

である。

---

今回のPC内部：

```text
あなたのPC
 ├ ブラウザ
 └ Live Server
```

---

## ブラウザ

通信を送る側。

```text
クライアント
```

と呼ばれる。

---

## Live Server

通信を待ち受ける側。

```text
サーバー
```

と呼ばれる。

---

# ローカル通信

今回は：

```text
同じPC内
```

で通信している。

これを：

```text
ローカル通信
```

という。

---

# HTTP通信の流れ

ブラウザ：

```text
test.html をください
```

↓

Live Server：

```text
はい、どうぞ
```

↓

ブラウザ表示

これがHTTP通信。

---

# DevTools を開いた

ショートカット：

```text
F12
```

---

# Networkタブ

ブラウザが実際に行った：

```text
HTTP通信記録
```

を見れる場所。

---

# Request / Response を観察

Network → test.html をクリック。

通信詳細を確認した。

---

# Request URL

```text
http://127.0.0.1:5500/test.html
```

意味：

```text
どこへ通信したか
```

---

# Request Method

```text
GET
```

意味：

```text
データをください
```

---

# GET理解

ブラウザ：

```text
test.html をください
```

とサーバーへ送っている。

---

# Status Code

```text
304 Not Modified
```

意味：

```text
前回と変更ない
```

---

# 200 と 304 の違い

## 200 OK

通常。

```text
ファイル本体を返す
```

---

## 304 Not Modified

```text
変更ないので、
PC側キャッシュを使ってください
```

という意味。

---

# キャッシュとは

ブラウザが：

```text
以前取得したデータ
```

をPCへ保存する仕組み。

目的：

- 通信量削減
- 表示高速化
- サーバー負荷軽減

---

# 今回起きたこと

ブラウザ：

```text
変更ありましたか？
```

↓

Live Server：

```text
変わってません
```

↓

304 Not Modified

↓

ブラウザがPC内キャッシュを使用

---

# User-Agent

```text
Mozilla/5.0 ...
```

意味：

```text
私はこのブラウザです
```

という自己紹介。

ブラウザは自分の情報も送っている。

---

# Day1で理解した本質

```text
Webページを見る
↓
ブラウザがHTTP通信する
↓
サーバーが返す
↓
ブラウザが表示する
```

Webの正体は：

```text
HTTP通信
```

である。

---

# Day1 最重要理解

```text
Webページを見る = 通信している
```