# docker-express

Docker + Express.js + PostgreSQLを使用したNode.jsアプリケーションのサンプルプロジェクトです。

## 技術スタック

- **Node.js**: 20
- **Express.js**: 5.2.1
- **PostgreSQL**: 13
- **Docker & Docker Compose**

## プロジェクト構成

```
docker-express/
├── app.js              # Expressアプリケーションのエントリーポイント
├── package.json        # Node.jsの依存関係
├── Dockerfile          # Dockerイメージの定義
└── docker-compose.yaml # マルチコンテナ構成の定義
```

## 必要な環境

- Docker
- Docker Compose

## セットアップと起動

1. リポジトリをクローン（または既にダウンロード済みの場合はスキップ）

2. Docker Composeでコンテナを起動

```bash
docker-compose up --build
```

3. アプリケーションにアクセス

ブラウザで以下のURLを開く：
```
http://localhost:3000
```

「Hello, World!」が表示されます。

## コンテナ構成

### webコンテナ
- Node.jsアプリケーション
- ポート: 3000
- コンテナ名: `my-node-app`

### dbコンテナ
- PostgreSQL 13
- パスワード: `password`
- コンテナ名: `postgres-db`
- データ永続化: `pgdata`ボリューム

## コマンド

### コンテナの起動
```bash
docker-compose up
```

### バックグラウンドで起動
```bash
docker-compose up -d
```

### コンテナの停止
```bash
docker-compose down
```

### ログの確認
```bash
docker-compose logs -f
```

### コンテナの再ビルド
```bash
docker-compose up --build
```

## 開発

ソースコードは`./`（カレントディレクトリ）が`/usr/src/app`にマウントされるため、ローカルでファイルを編集すると、コンテナ内にも反映されます。

ただし、変更を反映させるにはコンテナの再起動が必要です：
```bash
docker-compose restart web
```
