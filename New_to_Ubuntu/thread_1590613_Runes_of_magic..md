---
title: "Runes of magic."
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Rician on 2010-10-08
Hello! i am trying to download Runes of magic from their site. But the FOG  downloader Crashes at 26 MB. How can i fix this?  Runes of magic has encountered a critical  error and needs to be closed...

Help please?

Thanks.

---

### Post by P4man on 2010-10-08
Have a look here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20227](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20227)

To install winetricks, run this in a terminal:
```
wget http://www.kegel.com/wine/winetricks
```
then

```
winetricks
```

and select the packages suggested on winehq.

---

