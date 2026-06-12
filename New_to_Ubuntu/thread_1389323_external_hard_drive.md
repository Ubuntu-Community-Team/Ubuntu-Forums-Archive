---
title: "external hard drive"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by computerguts on 2010-01-24
I have a WD external hard drive. The size is one TB and I use it for my back up drive. It is about two years old. It will not recognize on computer. I tried it in windows xp and it wont show up in my computer, safely remove hard ware or disk management. I had this happen to me once before. But the difference then was that it did not show up in computer but it showed up in safely remove hard ware and disk management. Do you have any idea what might be the problem and what a solution might be. 

Thanks

---

### Post by mikewhatever on 2010-01-24
Could be the file system, but we don't do Windows support here. If you have Ubuntu, post the output of the command below from a terminal.

sudo fdisk -l

---

### Post by computerguts on 2010-01-24
here are the results from the command in the terminal window 

porter@porter-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 256 MB, 256901120 bytes
16 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         980      250864    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(978, 15, 32) logical=(979, 15, 32)
porter@porter-desktop:~$

---

### Post by chewearn on 2010-01-24
It's:
```
sudo fdisk -l
```

The option "-l" is the letter "el" not number one.

---

### Post by theozzlives on 2010-01-24
> **computerguts said:**
> here are the results from the command in the terminal window 

porter@porter-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9324    74894998+  83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 256 MB, 256901120 bytes
16 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         980      250864    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(978, 15, 32) logical=(979, 15, 32)
porter@porter-desktop:~$

If sdb is the drive, I'm wondering how sdb1 could be FAT32. If thats a second internal, or a flash drive then that would explain it. If the drive isn't showing up, then the first thing I'd do is replace the USB cable (providing you hear it spin-up when turned on).

---

### Post by computerguts on 2010-01-24
its a flash drive 

I don't here it spin or start up

---

### Post by lotharmat on 2010-01-24
1 Terrabyte flash?????

Are you sure?

---

### Post by theozzlives on 2010-01-24
Flash don't go to 1 TB, if it did it'd prolly cost thousands of dollars! SSDs don't even go that high! I think you mean 1 GB, 2 years... it's prolly just old and wore out. Flash Drives don't last forever. I can pick up a 4 GB at Office Depot for 14.99.

---

### Post by lotharmat on 2010-01-24
Is it a 1 Gigabyte flash drive?

---

### Post by capitalfear on 2010-01-24
i wish i had a 1T flash drive...and he said a ex hard drive...i have a 1t hard drive not external...but umm to be productive on this forum i would look for a "free registry fixer" and it fixes all the big registry problems for free and the tiny ones you have to pay for...hey go for it lol

---

### Post by Mariane on 2010-01-24
I answered to him there: 
[http://ubuntuforums.org/showthread.php?p=8717301#post8717301](http://ubuntuforums.org/showthread.php?p=8717301#post8717301)

Mariane

---

### Post by computerguts on 2010-01-24
Its a 1tb external hard drive, not a flash drive

---

### Post by computerguts on 2010-01-24
a good registry cleaner is cc cleaner. It also has some other useful functions. You will have to download wine though to use it in Ubuntu because it is a windows .exe file and not a deb package

---

### Post by mikewhatever on 2010-01-24
> **computerguts said:**
> a good registry cleaner is cc cleaner. It also has some other useful functions. You will have to download wine though to use it in Ubuntu because it is a windows .exe file and not a deb package

Ubuntu has no registry, so what are you going to clean?

---

### Post by computerguts on 2010-01-24
my mistake, I am still adjusting to linux

---

### Post by lotharmat on 2010-01-25
> **computerguts said:**
> Its a 1tb external hard drive, not a flash drive


So explain this then


> **computerguts said:**
> its a flash drive 

I don't here it spin or start up

---

