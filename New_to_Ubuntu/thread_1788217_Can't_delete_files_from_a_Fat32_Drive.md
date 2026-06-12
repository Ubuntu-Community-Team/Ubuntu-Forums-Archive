---
title: "Can't delete files from a Fat32 Drive"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by Mossring on 2011-06-22
I have a Ubuntu desktop with a second FAT32 drive. The owner of this drive is Root and therefore I can't change permissions. This means I can't delete files. How do I get around this?
I wanted a Windows format drive so I can use it on a network with my Windows laptop.

---

### Post by iclestu on 2011-06-22
> **Mossring said:**
> I have a Ubuntu desktop with a second FAT32 drive. The owner of this drive is Root and therefore I can't change permissions. This means I can't delete files. How do I get around this?
I wanted a Windows format drive so I can use it on a network with my Windows laptop.

cant you just start your file manager as root?
```

gksudo nautilus
```
for gnome or

```
kdesudo dolphin
``` for KDE

---

