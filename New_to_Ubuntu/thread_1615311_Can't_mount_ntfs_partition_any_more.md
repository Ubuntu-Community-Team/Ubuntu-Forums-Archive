---
title: "Can't mount ntfs partition any more"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by rcbinwi on 2010-11-06
I used to have my XP partition auto-mount when I had Ubuntu 9.04 on my Inspiron e1405.  Firefox had no problem using the profile on XP.  Now that I upgraded to 9.10, I can't access that partition for read/write access.  I can't fix the permissions.  I can only read.  So Firefox can't run off of it.  Similarly, I can't modify any document on that partition.  I tried mounting it through Nautilus as root and through pysdm/Storage Device Manager.  No luck.  Here's the message I get if I try to mount it through Nautilus not from root:

> Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)


I tried putting in a USB drive, and I have no problem with rw privileges.  So the problem seems isolated to my NTFS drive.

Any suggestions?

---

### Post by rcbinwi on 2010-11-06
I used ntfs-config, and it seems to have worked.  However, now I can only unmount the partition as root.  This is a new development, too.

---

