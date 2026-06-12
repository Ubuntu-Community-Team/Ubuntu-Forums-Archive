---
title: "Bookmarks folder"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Jynxx on 2009-03-26
Where would I locate the folder that houses my bookmarks for Firefox?

Thanks!

---

### Post by bwhite82 on 2009-03-26
~/.mozilla/firefox/*.default/bookmarks.html

---

### Post by lovinglinux on 2009-03-26
> **Soldierboy said:**
> ~/.mozilla/firefox/*.default/bookmarks.html

Since Firefox 3.0 the bookmarks are stored in a sqlite database:* ~/.mozilla/firefox/*.default/places.sqlite*

You can export to html tho, using the bookmark manager and you can also find backups under *~/.mozilla/firefox/*.default/bookmarkbackups/*

---

### Post by Jynxx on 2009-03-28
Is there a way to save my bookmarks? I'm wanting to reinstall Ubuntu and don't want to loose my bookmarks.

---

### Post by Ms_Angel_D on 2009-03-28
Install the [foxmarks]("https://addons.mozilla.org/en-US/firefox/addon/2410") extension it will back them up online then after you reinstall just reinstall the extension, you'll have all your bookmarks in place. Also if you don't want to lose your firefox extensions you can check out the [FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109") extension. It makes back ups of your entire firefox.

---

