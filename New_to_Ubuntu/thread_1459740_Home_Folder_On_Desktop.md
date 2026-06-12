---
title: "Home Folder On Desktop"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by eaglemob on 2010-04-21
Sorry to make this Thread.
I just installed ubuntu 10.04  64 bits. And i forgot how to put the home folder to appear on the desktop, not as a link but permanent.
Any help appreciated.

Thx

---

### Post by -humanaut- on 2010-04-21
Go to places and drag the home folder onto the desktop

---

### Post by linuxman94 on 2010-04-21
Open up a terminal (applications -> accessories -> terminal) and paste this command into it.

```
gconftool-2 --type Boolean --set /apps/nautilus/desktop/home_icon_visible True
```

---

### Post by eaglemob on 2010-04-21
Yea , i know that. But that is a link, is not the folder self :):(.

Linuxman94 !!! works !!

Tankx mate

---

