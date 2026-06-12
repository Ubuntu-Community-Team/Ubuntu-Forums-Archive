---
title: "Windows boots automatically, no matter what."
date: 2009-03-11
forum: New to Ubuntu
---

### Post by ClaytonOT on 2009-03-11
Alright,

I just installed OpenSUSE on a partition aside my Windows partition. Ubuntu is on its own device completely.

> 
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27024   217062247    7  HPFS/NTFS
/dev/sda2           29658       30394     5919952+   5  Extended
/dev/sda3           27024       29657    21157574   83  Linux
/dev/sda5           29658       30394     5919921   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x656237b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29657   238219821   83  Linux
/dev/sdb2           29658       30394     5919952+   5  Extended
/dev/sdb5           29658       30394     5919921   82  Linux swap / Solaris


SDA1 = Windows
SDA3 = OpenSUSE
SDB1 = Ubuntu

When I originally booted after my SUSE install I couldn't launch Ubuntu due to an Error 15 from GRUB. So I checked to make sure Windows was running and then it run chkdsk which from there I haven't been able to launch GRUB at all.

I've attempted the;
"root (hdA, B) - setup" method
The;
"Overwriting the Windows bootloader" method
and the;
"Recovering grub automatically + configuring grub" method

Nothing has worked. Windows continues to boot automatically.

---

### Post by ClaytonOT on 2009-03-11
Update:

I guess OpenSUSE moved GRUB to it's device... so I go it working... with OpenSUSE and Windows....

However, I'm getting an Error 15 with every boot option of Ubuntu so I still need help with that.

> ###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sdb1)###
title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sdb1)
    root (hd1,0)
    configfile /boot/grub/menu.lst

---

### Post by louieb on 2009-03-11
Easiest way is to use the configfile option to load Ubuntu's grub menu.
add this to opensuse's menu - you nearly had it right.
```
title Ubuntu grub menu
configfile (hd1,0)/boot/grub/menu.lst  
```

---

### Post by ClaytonOT on 2009-03-11
Well I added that to my menu list and it acts the same way as

> ###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sdb1)###
title Ubuntu 8.10, kernel 2.6.27-11-generic (/dev/sdb1)
    root (hd1,0)
    configfile /boot/grub/menu.lst


Both of them open up to my original looking GRUB menu (openSUSE's is more aesthetic) - but I still get an Error 15 trying to boot it.

Honestly, I'm not even sure if a /boot/grub/ exists on my Ubuntu partition now. Ive wandered into my /boot folder and all I saw was the kernel boot. Vmlinux-2.6.27 (plus various versions of it)

So grub/menu.lst does not exist? Unless that only refers to the config file on my OpenSUSE partition, since that's the one thats acting as the boot manager.

---

### Post by ClaytonOT on 2009-03-11
Well, I just decided to remove OpenSUSE and restore GRUB on my MBR. Everything's good now.

---

