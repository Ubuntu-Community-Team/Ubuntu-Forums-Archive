---
title: "VLC broken package"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-09-23
E: /var/cache/apt/archives/libvlccore2_1.0.2-1~ppa1_i386.deb: trying to overwrite `/usr/lib/libvlccore.so.2.1.0', which is also in package libvlccore0

Whilst uploading the latest updates, I got the message above. I tried deleting the offending file from my system...but I still get the same message, I tried fixing the broken package using Synaptic....still get the same message.....what gives?

---

### Post by Bachstelze on 2009-09-23
Someone should learn how to package properly... Anyway, what happens if you try to uninstall libvlccore0?

---

### Post by dunbrokin on 2009-09-23
I tried uninistalling...and that worked...except now I cannot reinstall..I just get the same message!!

---

### Post by Tekmoor on 2009-09-25
I'm having similar problems, and I noticed another thread about the same issue... anyone have a solution?

---

### Post by Jellyffs on 2009-09-26
Same here...

I tried to repair the packages it said:

```
W: Ignoring Provides line with DepCompareOp for package libva
```

I then uninstalled vlc and exaile (i think it uses that library too..?).

libvlccore2 installed correctly in the same process (I couldn't unselect it)...

I then installed vlc and exaile without problems.

Good luck.

Alex.

---

### Post by Tekmoor on 2009-09-26
Okay I uninstalled vlc and it's associated packages and reinstalled it and now it's fixed!

---

