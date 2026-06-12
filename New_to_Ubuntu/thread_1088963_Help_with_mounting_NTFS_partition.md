---
title: "Help with mounting NTFS partition"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by jarhead8286 on 2009-03-06
I have just installed Ubuntu on my son's Dell laptop and trying to mount NTFS partition.  What should I add to fstab file?

I have already created /media/NTFS directories.

ntfs-config only detects device /dev/sda2 on mount point /media/RECOVERY

executing "sudo fdisk -l" gives this:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15        1320    10485760    7  HPFS/NTFS
/dev/sda3            1321       38912   301957740    f  W95 Ext'd (LBA)
/dev/sda5            1321       38912   301957708+   7  HPFS/NTFS


```

---

### Post by taurus on 2009-03-06
```
/dev/sda5   /media/NTFS   ntfs-3g  defaults,locale=en_US.UTF-8  0  0
```

---

### Post by jarhead8286 on 2009-03-06
Thanks taurus... that did it.

---

### Post by neanderthalman on 2009-03-06
Keep in mind that folder owners and permissions on your NTFS drive are set by your fstab entry.

> ntfs/vfat = permissions are set at the time of mounting the partition with umask, dmask, and fmask and can not be changed with commands such as chown or chmod.

    *

      I advise dmask=027,fmask=137 (if you user umask=000 all your files will be executable). More permissive options would be dmask=000,fmask=111. 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

