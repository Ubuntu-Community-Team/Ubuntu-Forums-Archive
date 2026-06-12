---
title: "Accessing NTSF drives?"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by FRuMMaGe on 2007-04-10
How can I access the files I have stored on my NTSF drives/partitions?

I've tried going through the /tmp folder but when I click on the drive it says I don't have the relevant permissions to view it.

Please help :(

---

### Post by rajko on 2007-04-10
Thing is that in linux you need to mount them.
To mount them you need to know on which partition it is:
use (you must be root or append sudo in front of commands):
fdisk -l
Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         243     1951866   82  Linux swap / Solaris
/dev/hda2   *         244        1459     9767520   83  Linux
/dev/hda3            1460       36481   281314215    f  W95 Ext'd (LBA)
/dev/hda5            1460        1981     4192933+  83  Linux
/dev/hda6            1982       36481   277121218+  83  Linux


now when you know which partition you wuold like to mount just write:
mount /dev/hda3 /mnt/windows -t ntfs -r

if you need to mount them each time ubuntu starts edit /etc/fstab file.

rajko

---

