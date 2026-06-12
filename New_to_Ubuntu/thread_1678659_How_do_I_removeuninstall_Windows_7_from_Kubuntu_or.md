---
title: "How do I remove/uninstall Windows 7 from Kubuntu or Ubuntu?"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by Valkyr333 on 2011-01-30
Hi, everyone...

So I've just started with Linux Ubuntu (making the switch from Gnome to KDE at the moment), but I'm feeling confident enough with Linux that I'm comfortable with the idea of removing the Windows 7 OS that came with this computer (this was the plan to begin with.) This, of course, means I'm currently double-partitioned and am trying to get rid of Win7 and keep Linux. My problem is, any search I've done for how to go about this only turns up pages written for people who are trying to uninstall Win7 and go back to a previous version of Windows with which they're double-partitioned. I don't have any previous versions of Windows on this computer, just Win7 and Linux Ubuntu/Kubuntu. Is there a way to completely uninstall the Win7 OS from this computer if the only other installed OS is Linux?

Thanks!

-Val

---

### Post by lavinog on 2011-01-30
Removing the Windows partition should be all that is needed.
You can reinstall Ubuntu, and have it use the whole drive, or you can boot into the live cd and use gparted to remove the windows partition, then grow the ubuntu partition.

---

### Post by Mark Phelps on 2011-01-31
IF you're SURE that Ubuntu is in its own separate partitions, then go ahead an remove the Win7 partitions; but if you're not sure, then open a terminal in Ubuntu and run "sudo fdisk -lu" (that's a lowercase L, not a one).  

That will list your partitions.  IF you don't see any Ext4 partitions, then Ubuntu is installed INSIDE Windows and remove Windows will remove Ubuntu as well.

---

### Post by Valkyr333 on 2011-01-31
Should I assume that if there were any Ext4 partitions, it would specifically say "Ext4" somewhere in the results of that command line? I'm not sure what I'm looking at, but Ext4 doesn't turn up anywhere in said results.

---

### Post by sandyd on 2011-01-31
> **Valkyr333 said:**
> Should I assume that if there were any Ext4 partitions, it would specifically say "Ext4" somewhere in the results of that command line? I'm not sure what I'm looking at, but Ext4 doesn't turn up anywhere in said results.
it should just say "linux" under the system column.

or if you want the format as well...
```

blkid
```will work as well.
It should return something similar to```

sandy@sandyd-laptop ~ $ sudo blkid
/dev/sda2: UUID="bcb2f8a7-ea68-429b-a3b2-e7356f31f1bb" TYPE="ext4" 
/dev/sda3: UUID="5ad0dd0c-59dc-416b-8c25-c0d6e9ca5b6a" TYPE="swap" 
/dev/sda1: UUID="bb4289c7-3b36-4cfd-a7b0-b904501fa770" UUID_SUB="f166c11a-56f2-4691-9f78-d85642d4c01b" TYPE="btrfs" 

```
Except that I have a different partition setup, so the info above will differ. and I use btrfs instead of ext4 as well.

---

### Post by Valkyr333 on 2011-01-31
Under "System" it reads "Unknown" and then the next two columns under that both read "HPFS/NTFS"

---

### Post by smudge85 on 2013-02-24
I used the windows installer to install Kubuntu. I wanted to have a dual boot initially, but since Win7 uses such much space I'd like to have a virtual windows running (stripped down version to run MS Office for school).

Fdisk shows me this info:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78c7d9c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   234440703   117116928    7  HPFS/NTFS/exFAT

```

Any way to delete windows without deleting my current Kubuntu install?

---

### Post by oldos2er on 2013-02-24
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

