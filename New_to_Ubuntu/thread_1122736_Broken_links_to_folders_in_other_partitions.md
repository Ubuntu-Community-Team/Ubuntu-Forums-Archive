---
title: "Broken links to folders in other partitions"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by quickshot1012 on 2009-04-11
I have a link to a folder inside a windows xp partition. The only problem is, it only works after I access the drive through Places > IBM_PRELOAD (where it is stored). Do I have to mount the drive before I can use the link?

---

### Post by SuperSonic4 on 2009-04-11
Yeah, it needs to be mounted. You *can* use fstab to automount it on boot although ntfs-config is easier for beginners to use.

When a drive is not mounted it's treated as though it's not there.

---

