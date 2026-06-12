---
title: "Startups"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by anand warik on 2011-03-05
I work with Ubuntu 8.04. I have a partition (media/Anand) which always needs to be loaded when i am logged in since most of the applications are saved in this partition.How can I automate this process.

---

### Post by mikewhatever on 2011-03-05
What file system does it have? Here is a good howto for ntfs and fat32 partitions.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by a2warik on 2011-03-05
My system though 8.04 it shows entries in this type

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=41dd17de-bfbf-44c0-ab6d-04133b1e67fd /               ext3    relatime,erro$
# /dev/sda8
UUID=ce9ae82d-0cf7-4391-9113-e612a9795a3b /home           ext3    relatime     $
# /dev/sda7
UUID=223458fe-d2ef-4425-b6e5-85bf960f304f none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



It doesn't show they file system that i want to mount which is i assume sda5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        4869    39110211    f  W95 Ext'd (LBA)
/dev/sda5            3061        4869    14530761    b  W95 FAT32
/dev/sda6               1        1216     9767425+  83  Linux
/dev/sda7            1217        1459     1951866   82  Linux swap / Solaris
/dev/sda8            1460        3060    12860001   83  Linux


How do i find UUID part for the sda5?

---

### Post by el_koraco on 2011-03-05
> **a2warik said:**
> How do i find UUID part for the sda5?

type sudo blkid in the terminal. or sudo vol_id -u /dev/sda5, if that doesn't work.

---

### Post by mikewhatever on 2011-03-05
Sda5 has fat32 file system:
```
/dev/sda5 3061 4869 14530761 b W95 **FAT32**
```

---

### Post by anand warik on 2011-03-05
Thank You all, now I don't have to mount it explicitly.:D

---

