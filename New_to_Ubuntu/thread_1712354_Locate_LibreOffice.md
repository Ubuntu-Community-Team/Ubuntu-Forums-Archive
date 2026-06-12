---
title: "Locate LibreOffice"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by corto_be on 2011-03-22
Hi
In order to use Zotero on LibreOffice, I have to chose the LibreOffice Installation directory. I have no idea where to look for.
Thanks

---

### Post by vanadium on 2011-03-22
```

vanadium@vanadium:~$ ls $(which soffice)
/usr/bin/soffice
vanadium@vanadium:~$ ls $(which soffice) -l
lrwxrwxrwx 1 root root 34 2011-03-01 13:26 /usr/bin/soffice -> ../lib/libreoffice/program/soffice
vanadium@vanadium:~$ 

```
So I guess it will be /lib/libreoffice/program/

---

### Post by Dutch70 on 2011-03-22
Try your thread title in the terminal :lolflag:

```
locate libreoffice
```

Hopefully that will tell you what you need to know, although it will probably come up with a long list.

Also, check out this thread, not sure if it affects you or not.
[[COLOR="Blue"]http://forums.zotero.org/discussion/16050/zotero-standalone-libreoffice-plugin-firefox-could-not-load-plugin/[/COLOR]]("http://forums.zotero.org/discussion/16050/zotero-standalone-libreoffice-plugin-firefox-could-not-load-plugin/")

_

---

### Post by MrWES on 2011-03-22
I'd run this first

sudo updatedb

then use locate

---

