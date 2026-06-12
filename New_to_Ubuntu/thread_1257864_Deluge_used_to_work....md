---
title: "Deluge used to work..."
date: 2009-09-04
forum: New to Ubuntu
---

### Post by sillyboy on 2009-09-04
I'm using 8.04.  Deluge used to work great, but no more. I read the forums and tried: Reinstalling Deluge from the SPM. The SPM was showing that Deluge was installed (the green box), but there was no version # listed as is usually the case when a package is installed in Ubuntu.  I tried the console: sudo apt-get install Deluge.  Results: Reading state information... Done E: Couldn't find package Deluge. I went to the add/remove Apps:  The box is checked, meaning it is installed in Ubuntu.

I give up.  Any advice would be appreciated. :)

Thanks :D

---

### Post by mbzn on 2009-09-04
try to uncheck it then apply, update the db and install it again. I cant say that this will work but it's worth a try.

---

### Post by sillyboy on 2009-09-04
RESOLVED:  Thanks mbzn!

---

### Post by lovinglinux on 2009-09-05
> **sillyboy said:**
> RESOLVED:  Thanks mbzn!

BTW, the correct command is:

```
sudo apt-get install deluge-torrent
```

---

