---
title: "[SOLVED] hardy wireless drivers wont install"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by KDE_rocks2345 on 2008-06-20
Kubuntu Hardy, KDE3 version

I have already allowed third party content, however, when I try to install what I need, it said please insert disk, *inserts disk*

then I find myself in a loop
plz help

---

### Post by wormser on 2008-06-20
You need to disable CDrom.  It should be near the place you enabled the repositories.  Or by the command line.  Comment out the CDrom line.

```
sudo nano /etc/apt/sources.list
```

---

### Post by KDE_rocks2345 on 2008-06-20
Yay! it works now thanks.

---

