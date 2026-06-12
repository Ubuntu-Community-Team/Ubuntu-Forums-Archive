---
title: "Triple boot system doesn't show Ubuntu"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by metalmickey on 2011-05-01
Hi
I currently have a setup that includes Windows 7 & linux Mint on a 50/50 share of my Main Drive.
After a quick browse of the live CD I wanted to install Ubuntu straight away.
I was expecting to lose my copy of Mint in the process & made sure to back up Win7 stuff. However I was pleasantly surprised to find that during install the windows partition was safely hidden & i was given an option to install Ubuntu by reducing the size of Mint.
Perfect!

After install I booted to Windows, which was fine, booted into Mint fine, but poor old Ubuntu is nowhere to be seen!

The current Grub menu is the one from Mint, which has no mention of Ubuntu.

I thought I would have had an updated menu to include Ubuntu??

anyway that's enough waffle, here is a list shown after I ran fdisk -ls under mint, I hope it shows something?

```
dad-mint dad # fdisk -ls

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7a4bf9ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       14593   117218241    5  Extended
/dev/sda5               1       14593   117218209+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3f188d72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       60807   488328052+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3           60807      121602   488330241    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sdb5           60807       92992   258523967+  83  Linux
/dev/sdb6          120135      121602    11781120   82  Linux swap / Solaris
/dev/sdb7           92992      119617   213865472   83  Linux
/dev/sdb8          119617      120135     4157440   82  Linux swap / Solaris

Partition table entries are not in disk order
dad-mint dad # 

```

I have no idea how to solve this but would really like to get going with Ubuntu....

Any help would be gratefully appreciated.

Thanks

---

### Post by Vaphell on 2011-05-01
try running ```
sudo update-grub
``` in mint. It will run all autodetection scripts and create new menu cfg.

---

### Post by metalmickey on 2011-05-01
Wow, really that simple?
I'll give it a go....

Yep worked fine, posting from Ubuntu now :D

Another quick one though, in the list I now have:
Mint
Win7
Ubuntu

How can I get it to show
Ubuntu
Mint
Win7
so that it will auto select if I miss the countdown?
Without getting too complicated!!

---

### Post by Vaphell on 2011-05-01
mint is the bawss on your computer (it owns grub) so it will be listed first, the rest is listed in other systems section.
but if you want to set ubuntu as default, edit /etc/default/grub
```
gksu gedit /etc/default/grub
```
change this line (counting lines from 0)
```
GRUB_DEFAULT=0
```
run sudo update-grub to apply changes
note that additional kernels after upgrades will require corrections.

You could fix it permanently by setting up grub in ubuntu and disabling/removing in mint but i don't really know how to do that in detail.

---

### Post by ajgreeny on 2011-05-01
You can either install startup-manager which allows you to set the default system to boot, or you could alternatively start using the grub in Ubuntu, which will, of course put ubuntu first in the list.  You can also edit the /etc/default/grub file, but I am assuming hat if you want Ubuntu as the default booting OS, you will also want grub to be owned by Ubuntu, not Mint.

If you choose to do it the second way, simply boot to Ubuntu and run ```
sudo grub-install /dev/sda
```assuming the boot device is your first disk, sda.

To double check your current boot arangement click on the Boot-info-script link in my signature, and follow the instructions there, then copy the RESULTS.txt file back here in code tags.

---

### Post by metalmickey on 2011-05-01
Thank you both for your help & fast replies.
I think for a newcomer like me, startup-manager may be the best route.

Great community BTW.
Thanks Again, loving the unity desktop

---

