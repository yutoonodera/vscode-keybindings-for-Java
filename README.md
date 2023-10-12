## vscodeでCtrl + sでSystem.out.println("●●●●start●●●●" +  ""    + "●●●●end●●●●");を挿入する
Javaでよく使うスクリプトをショートカットで使えるように設定した。
1. Macだと Code>基本設定>Keyboard Shortcutsに移動
1. 右上をクリックするとkeybings.jsonが開く
1. 任意のshortcutを設定する

※VScodeの再起動は不要でkeybings.jsonの保存だけで良い


<img width="1026" alt="image" src="https://github.com/yutoonodera/vscode-keybindings-for-Java/assets/51279183/97bc597a-7ae3-416e-91ca-539d5806aa7c">



ココに書く

<img width="652" alt="image" src="https://github.com/yutoonodera/vscode-keybindings-for-Java/assets/51279183/a915f854-79a7-4704-9e7c-fed975c1a42a">

行末にフォーカスが当たるため`0`で行頭に移動して、`f + +` して1つ目 + に移動して`a`する

## System.out.println("●●●●start●●●●" +  ""    + "●●●●end●●●●");を削除する
1つのコマンドで検索&削除したかったができなそうなので2STEPに分ける

```
//1.System.out.println\(\"●●●●start●●●●というコンテキストを含むファイルを一意で抽出する
grep -rl System.out.println\(\"●●●●start●●●● ./ | xargs readlink -f
```

```
//2.ファイルパスを指定してSystem.out.println\(\"●●●●start●●●●というコンテキストを含む行を削除し、ファイルを上書き保存する
sed -i -e '/System.out.println("●●●●start●●●●"/d' 1.で抽出したファイルパス
```
