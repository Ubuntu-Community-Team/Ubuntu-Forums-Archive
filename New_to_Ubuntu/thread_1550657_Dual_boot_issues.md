---
title: "Dual boot issues"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by grubstub on 2010-08-11
Hi,

I'm a newcomer to linux and have swam thoroughly out of my depth. Any insights or advice you'd be able to provide would be hugely appreciated...

Having done a Wubi install of Ubuntu 10.04 from Windows XP I booted into linux without a problem. After then having installed the recommended updates (& graphics drivers) I rebooted only to be given a grub error; "Error: No such device ...", along with a "Grub rescue>" command prompt. To recover the system I booted from a Ubunutu LiveCD (v8.04.1 - the only 'proper' ubuntu CD I could get my hands on, as this finicky system refused to boot from any burned CDRs of newer iterations) which prompted a fresh install. Now back up & running, I updated Ubunutu to 10.04 from within itself, and have been running this without an issue since.

The problem is that since going through this roundabout process, Windows is no longer an option on the bootloader. I've tried adding the following to Grub's menu.lst to no avail:

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

When trying to load this option from grub I get the error "selected drive does not exist". The info given on the sudo fdisk -l command is the following:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf82bc96a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000230ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976761560    7  HPFS/NTFS


Worryingly, I see no reference to a Windows partition. Could this have been wiped on the install? Again, any advice or direction you could offer would be a massive help!

---

### Post by bcbc on 2010-08-11
> **grubstub said:**
> Hi,

I'm a newcomer to linux and have swam thoroughly out of my depth. Any insights or advice you'd be able to provide would be hugely appreciated...

Having done a Wubi install of Ubuntu 10.04 from Windows XP I booted into linux without a problem. After then having installed the recommended updates (& graphics drivers) I rebooted only to be given a grub error; "Error: No such device ...", along with a "Grub rescue>" command prompt. To recover the system I booted from a Ubunutu LiveCD (v8.04.1 - the only 'proper' ubuntu CD I could get my hands on, as this finicky system refused to boot from any burned CDRs of newer iterations) which prompted a fresh install. Now back up & running, I updated Ubunutu to 10.04 from within itself, and have been running this without an issue since.

The problem is that since going through this roundabout process, Windows is no longer an option on the bootloader. I've tried adding the following to Grub's menu.lst to no avail:

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

When trying to load this option from grub I get the error "selected drive does not exist". The info given on the sudo fdisk -l command is the following:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf82bc96a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000230ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976761560    7  HPFS/NTFS


Worryingly, I see no reference to a Windows partition. Could this have been wiped on the install? Again, any advice or direction you could offer would be a massive help!

The first problem would have been fixed by reinstalling the windows boot loader. See bug report here: [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

It seems like when you reinstalled (you said "which prompted a fresh install") you overwrote windows (assuming it was on the 100GB drive). 
You might be able to recover some data (if you have lost important data) - if this is the case, stop using the drive, boot from a live CD and use a tool like photorec. If your data is backed up, then you might just need to shrink your ubuntu partition and install windows again.

---

### Post by QLee on 2010-08-11
> **bcbc said:**
> The first problem would have been fixed by reinstalling the windows boot loader. See bug report here: [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

It seems like when you reinstalled (you said "which prompted a fresh install") you overwrote windows (assuming it was on the 100GB drive). 
You might be able to recover some data (if you have lost important data) - if this is the case, stop using the drive, boot from a live CD and use a tool like photorec. If your data is backed up, then you might just need to shrink your ubuntu partition and install windows again.

+1

That makes two of us who have read through the thread and who agree on a likely scenario if you let the install overwrite the Windows install. Sorry I can't offer better news.

---

### Post by grubstub on 2010-08-12
Thanks for your input guys. I had suspected as much, but thought it was worth running it past the experts first (which i'll do before reinstalling things next time!)

Thankfully everything's backed up so it's not nearly as disastrous as it could have been.

---

