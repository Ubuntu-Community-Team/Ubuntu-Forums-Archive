---
title: "Resizing partitions"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by winjeel on 2010-03-16
I've tried to resize my partitions on my dual boot (XP and 9.10) computer, but can't find a way to do it. I've tried to use gparted on the 9.04 livecd, but it doesn't show XP and 9.10 as separate partitions. Whilst 9.10 has 10Gb of space, which is now down to 400mb of space, of the whole hdd it has 45% free space. As you can imagine, it's frustrating having 25Gb free on the main hdd, but can't use it... yet.

I'm also quite busy, and so I don't want to lose the whole day playing around with this. I just need to work in 9.10, using e-mail, working on files, and importantly, install a new program for my research (Nvivo and livescribe on Wine).

Pertinent info, Dell Latitude D520; XP with 45Gb partition; Ubuntu 9.10 with 10Gb partition (want to increase to 15Gb); Gparted on Ubuntu 9.04 LiveCD; 1Tb external hdd (for documents and backups), with 95% free space.

Thanks in advance for your help.

---

### Post by Geoff918 on 2010-03-16
This might be a foolish question. But, did you do a Wubi install initially?

---

### Post by winjeel on 2010-03-16
Thanks for replying. I have no idea. I initially downloaded Ubuntu 9.04, burnt it to disk, then installed it onto this computer. It was my first time to use Ubuntu, and first time to make a partition on this computer. I just used whatever was in that 9.04 first-time install (and partition making) package.

---

### Post by bumanie on 2010-03-16
You post the output of > sudo fdisk -l from terminal from ubuntu. Go to Applications --> Accessories --> Terminal. Type in the quote and hit enter. Type in your password (there is no visual output for this) and then hit enter again. Copy and paste the output to the forum. That is a lower case L, not the digit one.

---

### Post by winjeel on 2010-03-17
Here:

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        7294    58548892+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcdb7f6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdb5               2      121601   976751968+   b  W95 FAT32

Disk /dev/sdc: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x504c520c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2431    19526976    c  W95 FAT32 (LBA)

---

### Post by Elfy on 2010-03-17
You would have a wubi install it appears - there are no linux partitions. You can resize the drive with LVPM, or move the /home to a seperate partition.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

You can also migrate to a normal partition and install

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

Hope that helps.

---

### Post by winjeel on 2010-03-18
I've been pretty busy, and so I haven't had time to look more into this. Also, what's concerning is, is that all other avenues have been exhausted so quickly, and so that "swap" needs to be done. What's also concerning is, is the lack of information, details on how to do the swap, what the swap does to the hdd, and clearer information on how to do the swap. The information is very unclear, and is not meeting what was promised when I first signed up to Ubuntu. For first timers using dual boot, there were assurances that the partition size can be adjusted, but when this promise is made to first time Ubuntu users, one would assume that it's hassle free and doesn't cost much time. I'm afraid to say that I don't have much time to mess around from now until summer (August holidays).

---

### Post by winjeel on 2010-03-18
> **winjeel said:**
> I've been pretty busy, and so I haven't had time to look more into this. Also, what's concerning is, is that all other avenues have been exhausted so quickly, and so that "swap" needs to be done. What's also concerning is, is the lack of information, details on how to do the swap, what the swap does to the hdd, and clearer information on how to do the swap. The information is very unclear, and is not meeting what was promised when I first signed up to Ubuntu. For first timers using dual boot, there were assurances that the partition size can be adjusted, but when this promise is made to first time Ubuntu users, one would assume that it's hassle free and doesn't cost much time. I'm afraid to say that I don't have much time to mess around from now until summer (August holidays).


I just realised one of the causes of the problems... why I'm suddenly running out of space. UbuntuOne. I've been needing an offsite storage for a while, and a secure place to keep back ups of important documents. I've used about 700mb storing important documents and presentations, which is duplicated on my external hard drive, ubuntuone (and both laptops' hdd's). Hmm...

---

### Post by albert s on 2010-03-18
I think, as has been stated, you dont have a separate ubuntu install,
you have WUBI, which is in effect a ubuntu inside your windows, which is why you have NO room left.
you need to install ubuntu on its own partition, why I actually found to be the easiest way to do it, 
why anyone would find installing it inside windows easier I find hard to understand,
unless they downloaded the wrong programme, or booted it up wrong, instructions are there to be followed, unless you know better.

---

