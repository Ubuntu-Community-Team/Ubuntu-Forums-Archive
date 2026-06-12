---
title: "Have the pendrive vfat fat32 an UUID for /etc/fstab?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-06-21
Hello,

Have the pendrive vfat fat32 an UUID for /etc/fstab?

vol_id gives no UUID :(

---

### Post by eriktheblu on 2010-06-21
To find a UUID, try ```
sudo blkid
```

Are you wanting to permanently mount a pendrive? It should automatically mount under /media.

---

### Post by frenchn00b on 2010-06-22
> **eriktheblu said:**
> To find a UUID, try ```
sudo blkid
```

Are you wanting to permanently mount a pendrive? It should automatically mount under /media.

visibly for a pendrive it says no UUID but vfat

---

### Post by honeybear on 2010-09-20
> **frenchn00b said:**
> visibly for a pendrive it says no UUID but vfat

but why? even a floppy disk has a serial number, man !

---

