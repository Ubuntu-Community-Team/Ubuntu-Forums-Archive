---
title: "Update Manager Problem"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by MindController on 2010-04-08
I can't update from Update Manager. If i click check button i get this error

```

Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```
thx for reading my post and pls help.

---

### Post by perlluver on 2010-04-08
Go to System>Administration>Software Sources, and un-check use CD-Rom.  Then let it update again.

---

### Post by warfacegod on 2010-04-08
Or you could put your 9.10 Karmic CD into the drive. But it will give you the same error when you take the disc back out later.

---

### Post by MindController on 2010-04-08
> **warfacegod said:**
> Or you could put your 9.10 Karmic CD into the drive. But it will give you the same error when you take the disc back out later.
sure @warfacegod. I tried like @perlluver said but i still have this problem. What sould i do?

---

### Post by warfacegod on 2010-04-08
When you unchecked the 9.10 CD and clicked the close button, did a window open asking you to Reload? If so you'll need to do that. Then update.

---

