---
title: "20210307 Hugo re-setup trouble shooting"
date: 2021-03-07T10:35:50+09:00
draft: false
tags: ["Hugo","git submodule"]
---

# Hugo環境構築時のちょっとしたハマりごとのトラブルシューティング

手元環境のwslの環境が微妙などうさになってしまったので、
再構築した。  
その際にHugoの環境の構築で少しハマったのでメモ。  

単純にgit cloneして,hugoのバイナリを/usr/local/binに設置したところ以下のようなエラーが出た。  

```
found no layout file for "HTML" for kind "page": You should create a template file which matches Hugo Layouts Lookup Rules for this combination.
```
よくみるとgit submoduleで取得しているhugoのテーマリポジトリが中身が空でcloneに失敗している。  
git submoduleは別途以下のコマンドで内容を再帰的に取得する必要があるとのことであった。  
普段submoduleをあまり使わないので参考になった。  

```
git submodule update --init --recursive
```

# 参考資料
- https://stackoverflow.com/questions/60269683/how-to-fix-the-error-found-no-layout-file-for-html-for-page-in-hugo-cms
- https://qiita.com/kinpira/items/3309eb2e5a9a422199e9