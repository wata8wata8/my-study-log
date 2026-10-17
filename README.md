# 学習ログ

HTML/CSS/JavaScriptとlocalStorageだけで動く、学習の記録を残すアプリです。

日付ごとに学習の調子と「今日の学習メモ」を保存できます。数学の復習や英単語、読書メモなど、学習した内容を短く記録して振り返れます。記録はブラウザのlocalStorageに保存され、同じブラウザで再度開けば確認できます。

## 📱 デモ

🔗 [https://gigaschool.github.io/tiny-diary/](https://gigaschool.github.io/tiny-diary/)

![📷 image.png](image.png)

## デモの動かし方

`index.html` をブラウザで開くだけで使えます。ビルドやサーバー起動は不要です。

Live Serverで起動し、学習ログの保存・編集・削除、検索、調子による絞り込みが動作することを確認しています。

```text
tiny-diary/
├── index.html
├── styles.css
├── app.js
├── README.md
└── LICENSE
```

## 機能

- 今日の日付を自動セット
- 今日の調子を5種類から選択
- 今日の学習メモを保存
- 日付ごとに1件の記録として保存
- 同じ日付で保存すると上書き
- 過去ログの一覧表示
- 保存済みログの編集
- 保存済みログの削除
- 学習メモ検索
- 調子による絞り込み
- 最近7件の学習の調子を表示する波形グラフ
- スマートフォンで入力欄と最新の学習ログを見やすく表示

## 使用技術

- HTML
- CSS
- JavaScript
- localStorage

外部ライブラリは使っていません。

## localStorage

保存キーは `tiny-diary.entries.v1` です。

データは次のような配列で保存されます。

```json
[
  {
    "id": "example-id",
    "date": "2026-04-29",
    "mood": "happy",
    "note": "数学の平方根を復習。英単語を10個覚えた。",
    "createdAt": "2026-04-29T10:00:00.000Z",
    "updatedAt": "2026-04-29T10:00:00.000Z"
  }
]
```

## 学習の調子

調子は次の5種類から選べます。

| 値 | 表示 | スコア |
| --- | --- | --- |
| `happy` | 集中できた | 5 |
| `calm` | 順調だった | 4 |
| `normal` | ふつう | 3 |
| `tired` | 少し疲れた | 2 |
| `sad` | あまり進まなかった | 1 |

最近7件の記録をこのスコアに変換して、学習の調子の変化をSVGの波形グラフとして表示します。

## 教材で説明しやすい流れ

1. フォームから値を受け取る
2. JavaScriptの配列に学習ログを追加する
3. `JSON.stringify` でlocalStorageへ保存する
4. `JSON.parse` でlocalStorageから読み込む
5. 配列をもとに一覧と学習リズムを再描画する

## ファイル構成

- `index.html`: 画面の構造
- `styles.css`: レイアウトと見た目
- `app.js`: 保存、表示、編集、削除、検索、絞り込み、学習リズム描画
- `README.md`: この説明ファイル
- `LICENSE`: MITライセンス

## ライセンス

MIT License
