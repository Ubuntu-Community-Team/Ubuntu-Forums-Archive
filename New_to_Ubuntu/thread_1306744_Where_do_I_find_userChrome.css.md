---
title: "Where do I find userChrome.css ?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Ericx25 on 2009-10-30
It seems that I need to edit ~/.mozilla/firefox/<random>.default/chrome/userChrome.css
 to change the font of the Bookmarks toolbar.

My question : 
Where do I find the  ~/.mozilla..... ? (I don't understand the file system on Linux)

Thanks for your help

Eric

(Every now and then I download a copy of Ubuntu to see if it is usable by a non IT user (like me).
Every time I come to the same conclusion : NO.

---

### Post by zvacet on 2009-10-30
> Where do I find the ~/.mozilla..... ?

It is hidden in your home directory.To see it ctrl+h and you will see all hidden files and folders in your home directory.Your random<default> have name and you will see it under ~/.mozilla directory.To edit that file type in applications>accessories>terminal

```
gksudo gedit ~/.mozilla/firefox/<random>.default/chrome/userChrome.css
```

In this line you will replace **<random>.default** with real name of that folder (for example f8jzb1ff.default).

---

