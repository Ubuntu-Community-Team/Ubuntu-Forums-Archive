---
title: "How can I back up/clone a &quot;recovery partition&quot;? (Lenovo Y500 OneKey Recovery)"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by KIAaze on 2011-01-04
Hi,

I want to set up a dual-boot Vista/Ubuntu on a Lenovo Y500 for someone.

After problems with gparted not starting from USB-key and Live-CD (solved by [upgrading the gparted package]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885")), I am finally at the partitioning step.

However, it seems there is an unknown 11.91 GiB partition, as well as 2.49 MiB of unallocated space.
From what I read, those 11.91 GiB are for the "OneKey Recovery" system.

I would like to backup/clone this partition to an external HD before partitioning just to be safe.
How can I do that?

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       13038    84244860    f  W95 Ext'd (LBA)
/dev/sda3           13039       14593    12490537+  12  Compaq diagnostics
/dev/sda5            2551       13038    84244828+   7  HPFS/NTFS

```

---

### Post by mikewhatever on 2011-01-04
You could use a Clonezilla live cd/usb. On the second though, Parago's Barckup&Recoverry for Windows is an easier option.
[http://www.paragon-software.com/home/db-express/download.html](http://www.paragon-software.com/home/db-express/download.html)

---

### Post by KIAaze on 2011-01-04
Thanks. I already did the partitioning and installation now, but maybe I'll still try to make a partition image later.

Everything seems to work perfectly by the way.
Ubuntu 10.10 supports the Lenovo Y500 very well. :)
Suspend, hibernate, internal microphone and camera, desktop effects, wireless... Everything works!
I'm almost jealous it's not my PC.

The keyboard didn't work at first boot, but worked afterwards. Strange bug.
The touchpad worked after adding "i8042.reset" to the boot line:
[http://ubuntuforums.org/showthread.php?t=1601396](http://ubuntuforums.org/showthread.php?t=1601396)

---

### Post by www.rzr.online.fr on 2011-11-20
> **KIAaze said:**
> Hi,

I want to set up a dual-boot Vista/Ubuntu on a Lenovo Y500 for someone.



Can this  okr part be restored on an other different lenovo system ? I did lost my s10-3t okr partition too...

---

