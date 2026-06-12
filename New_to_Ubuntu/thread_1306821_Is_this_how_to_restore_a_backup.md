---
title: "Is this how to restore a backup?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by BikeHelmet on 2009-10-30
Oh hi,

Is this the proper way to restore a backup? My 9.04 -> 9.10 upgrade failed pretty spectacularly, but I did get it to boot. It's now telling me that my external HDD is an nVidia RAID array - I'm not even going to try writing files to it, but luckily I can still read part of it.

Will this restore everything to the way it was?
```
#!/bin/bash
tar xvpfj "/media/Storage_A3/UbuntuBackup/SystemBackup_091023.tar.bz2" -C /
mkdir proc
mkdir lost+found
mkdir media
mkdir mnt
mkdir sys

```

Just making sure, because I have a feeling I have one shot at going back to 9.04. :D I took and edited that script from another thread.

---

### Post by phillw on 2009-10-30
Did u use this thread ?

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Phill.

---

### Post by BikeHelmet on 2009-10-30
Yeah, that's the one. I didn't read all 97 pages, though.

Well, wish me luck. ;)

---

