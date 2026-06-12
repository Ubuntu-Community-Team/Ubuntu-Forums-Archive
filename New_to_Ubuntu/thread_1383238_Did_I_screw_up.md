---
title: "Did I screw up?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by shadowcrunch on 2010-01-17
Hello! I'm pretty sure I did something stupid and was hoping someone could verify, maybe toss out a solution. I had to format my desktop a few days ago, and after getting vista back on I decided to try a ubuntu dual-boot again (tried 2 years ago and enjoyed, but my laptop's wireless had no working linux drivers). Anyway, I used the automatic install of 9.10 and after about 5 hours of forums I finally got my network running. YAY! Then I tried installing linux drivers for my graphics card and lost all graphics acceleration.

I was reading in forums that installing ubuntu off a CD was better with drivers and such, so I downloaded the image. A few forums I read mentioned I could just throw the disc in and install over the "old" ubuntu, and tweak the partition size while I was at it. So my flow went vista, then downloaded ubuntu, then CD ubuntu. Now when I start up, I get two different OS selection screens, and my available disk space in vista looks like I actually have both ubuntu's still in there. Is there any way I can find out for sure? And if so, is there any way to get rid of the "old" ubuntu, reclaim the space, and not have to format the whole thing?

---

### Post by Sef on 2010-01-17
Applications > Accessories > Terminal

then copy and paste this code into the terminal:

```
Sudo fdisk -l
```

copy and paste the results here.

---

### Post by kenuf on 2010-01-17
In Ubuntu run GParted
System> Administration> GParted

It will let you see the patritions....  if there are two Ubuntu partitions that is where you'll see it, and can fix it.

---

### Post by admiralspark on 2010-01-17
> **kenuf said:**
> In Ubuntu run GParted
System> Administration> GParted

It will let you see the patritions....  if there are two Ubuntu partitions that is where you'll see it, and can fix it.

you have to run this from the LiveCD or install it with 
```
sudo apt-get install gparted
```

---

### Post by kenuf on 2010-01-17
> **admiralspark said:**
> you have to run this from the LiveCD or install it with 
```
sudo apt-get install gparted
```

That's right...  It's never made sense to me that it isn't in the standard install.

---

### Post by shadowcrunch on 2010-01-17
Okay, I don't have access to the desktop right now (wife's sleeping and me pounding on the keys will wake her up), but will try these things in the morning. I'll say thanks in advance just for offering help. So, thanks! I'll let you know what I find out.

---

### Post by shadowcrunch on 2010-01-17
Okay, first things first. I'm going down the line. Here's the terminal copy/paste of fdisk:
root@desktop:/home/mikori# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93019301

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21264   170803048+   7  HPFS/NTFS
/dev/sda2           21265       30401    73392952+   5  Extended
/dev/sda5           21265       30023    70356636   83  Linux
/dev/sda6           30024       30401     3036253+  82  Linux swap / Solaris
root@desktop:/home/mikori# 


heh...sda2 and 5 are thr gith size for my new ubuntu install, and sda6 is the right size for the old. Okay, on to the next.

---

### Post by shadowcrunch on 2010-01-17
Okay, aside from me reading sda6 wrong, here's what gparted is telling me:

/dev/sda1    ntfs           162.89GiB     Flags=boot
/dev/sda2    extended       69.99GiB
/dev/sda5    ext4           67.10GiB   Used=4.49GiB  Unused=62.61GiB
/dev/sda6    linux-swap     2.90GiB

Oh, and sda5 has a "mount point" of / (just the slash)

I have a 250GB drive, and when I installed ubuntu from the disc I set the partition at 70 GB. Oh, and now I see in gparted sda5 and sda6 are "inside" sda2. Looks like it did install over the old install, but that doesn't explain why I have two OS selection screens. Hmmmmm...

---

