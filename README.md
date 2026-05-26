# NEWT MCP

<!-- TODO: ヒーロー画像/GIF をここに配置（デザイナー作成中） -->

[newt.net](https://newt.net) のツアー・ホテル・目的地・空港検索を、Claude などの AI アシスタントから直接呼び出せる MCP（Model Context Protocol）サーバーです。

ホスト型のため、サーバーを自前で立てる必要はありません。プラグインを追加するだけで利用を開始できます。

---

## できること

- **ツアー** — 検索機能、詳細情報、出発日カレンダー、料金の取得、在庫の取得、NEWTツアーURLの取得、写真の取得
- **ホテル** — 検索機能、詳細情報、地域検索、料金の取得、部屋の取得、在庫の取得、NEWTホテル URLの取得、写真の取得
- **目的地・空港** — 検索、空港の検索、発着地の指示・検索、在庫の検索（ツアーのみ）

すべて [newt.net](https://newt.net) のリアルタイム在庫や料金を参照します。

## インストール

### Claude Code

```bash
/plugin marketplace add reiwa-travel/newt-mcp-server
/plugin install newt-mcp@newt
```

### Claude Desktop

カスタムコネクタとして以下の URL を追加してください:

```
https://mcp.newt-dev.net/mcp
```

または `claude_desktop_config.json` に直接記述:

```json
{
  "mcpServers": {
    "newt": {
      "type": "http",
      "url": "https://mcp.newt-dev.net/mcp"
    }
  }
}
```

### Cursor / その他の MCP 対応クライアント

サーバー URL（Streamable HTTP）:

```
https://mcp.newt-dev.net/mcp
```

## プロンプト例

- 「来月のバリ 4 日間のツアーを 15 万円以下で探して」
- 「8月1日からソウル出張、2泊3日、エコノミークラスで探して。予算は10万円で。」
- 「来週末の京都のホテルを5つ比較してください」
- 「来週の大阪出張、駅近で評価の高いホテルを教えて」
- 「12 月の沖縄旅行、家族 4 人のプランを組んで」

## 利用可能なツール

ロケール対応: `ja`（既定）、`ko`、`en-US`、`zh-Hant-TW`、`zh-Hant-HK`、`zh-Hans-CN`

### ツアー

| ツール | 説明 |
|--------|------|
| `tour_search` | 目的地・空港・日程・価格・座席クラス・特徴でツアーパッケージを検索 |
| `tour_detail` | ツアー詳細（プラン・フライト・ホテル・食事・行程） |
| `tour_detail_calendar` | 出発日・帰着日カレンダー |
| `tour_quotation` | 指定日の正確な価格、または日付なしでの価格レンジ |

### ホテル

| ツール | 説明 |
|--------|------|
| `hotel_search` | 日程・部屋数・地域で空室付きホテル検索 |
| `hotel_detail` | ホテル詳細（説明・設備・レビュー・地図） |
| `hotel_region_search` | 地域検索（都市・エリア・名所） |
| `hotel_region_detail` | 地域詳細（親・子・兄弟地域を含む） |

### 目的地・空港

| ツール | 説明 |
|--------|------|
| `destination_search` | 目的地検索 |
| `destination_detail` | 目的地詳細 |
| `airport_search` | 空港検索 |

## 利用規約

- 個人・商用を問わず**無料**でご利用いただけます。
- 本 MCP を組み込んだアプリケーションでは [newt.net](https://newt.net) へのリンク表示をお願いします。
- **SLA・保証はありません。** 予告なく仕様変更・停止する場合があります。
- 過度な負荷をかける利用には制限をかける場合があります。

## ライセンス

このリポジトリのコンテンツは [MIT License](./LICENSE) で公開しています。
NEWT のデータ・サービスの利用については上記「利用規約」をご参照ください。

---

Provided by [Reiwa Travel](https://newt.net) — 旅行をもっと自由に。
