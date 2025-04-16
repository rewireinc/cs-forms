# CS Forms

このリポジトリは、リワイア社のカスタマーサポートフォーム用HTMLファイルを管理するためのものです。現在、以下のサービス用フォームが含まれています：

- App Unity Safe Delete（アプリユニティセーフデリート）
- さんクス（thanx）
- Pafit問い合わせフォーム

## フォームスクリプトの修正手順

### 1. リポジトリのクローン

```bash
git clone https://github.com/rewireinc/cs-forms.git
cd cs-forms
```

### 2. フォームファイルの編集

以下のHTMLファイルを必要に応じて編集します：

- `au-safe-delete-cs.html` - App Unity Safe Delete用フォーム
- `thanx-cs.html` - さんクス用フォーム
- `au-inquiry.html` - Pafit問い合わせフォーム

### 3. フォームの主な編集ポイント

#### フォームのスタイル変更

スタイルは各HTMLファイルの`<head>`タグ内の`<style>`セクションで定義されています。例：

```html
<style>
  #zohoSupportWebToCase textarea, #zohoSupportWebToCase input[type='text'], ... {
    width: 280px;
  }
  /* その他のスタイル定義 */
</style>
```

#### フォームフィールドの変更

フォームフィールドは`<form>`タグ内の`<table>`内にあります。フィールドを追加・変更する場合は、以下の例を参考にしてください：

```html
<tr>
  <td nowrap class='zsFontClass hleft' width='25%' Top>
    フィールド名&nbsp;&nbsp;<br>
    <input type='text' maxlength='120' name='Field Name' value='' />
  </td>
</tr>
```

#### 必須フィールドの設定

必須フィールドは、JavaScriptの`zsWebFormMandatoryFields`配列で定義されています：

```javascript
var zsWebFormMandatoryFields = new Array("Subject","Contact Name","Email","Description");
var zsFieldsDisplayLabelArray = new Array("件名","氏名","メールアドレス","問い合わせ内容");
```

#### フォーム送信先の変更

フォームの送信先は`<form>`タグの`action`属性で指定されています：

```html
<form name='zsWebToCase_XXXXXXXXXXXXXXX' id='zsWebToCase_XXXXXXXXXXXXXXX' 
      action='https://desk.zoho.com/support/WebToCase' method='POST' ...>
```

#### 送信後のリダイレクト先の変更

送信後のリダイレクト先は`returnURL`という名前の隠しフィールドで指定されています：

```html
<input type='hidden' name='returnURL' value='https://rewireinc.github.io/cs-forms/thanx-cs.html'/>
```

### 4. 変更のコミットとプッシュ

```bash
git add .
git commit -m "フォームの変更内容を簡潔に記述"
git push origin main
```

### 5. GitHub Pagesでの確認

変更がマージされると、GitHub Pagesで自動的に公開されます。以下のURLで確認できます：

- App Unity Safe Delete: https://rewireinc.github.io/cs-forms/au-safe-delete-cs.html
- さんクス: https://rewireinc.github.io/cs-forms/thanx-cs.html
- Pafit問い合わせフォーム: https://rewireinc.github.io/cs-forms/au-inquiry.html

## 注意事項

- フォームのIDや隠しフィールドの値（`xnQsjsdp`、`xmIwtLD`など）は変更しないでください。これらはZoho Deskとの連携に必要です。
- フォームのスタイルを変更する場合は、全体のデザインとの整合性を確認してください。
- フォームフィールドを追加・削除する場合は、対応するJavaScriptの検証ロジックも更新してください。
