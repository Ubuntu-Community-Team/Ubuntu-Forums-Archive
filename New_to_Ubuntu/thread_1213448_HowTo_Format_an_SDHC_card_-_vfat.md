---
title: "HowTo Format an SDHC card - vfat"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by RadarBat on 2009-07-14
I am trying to format an SDHC flash memory card to vfat so I can use it as a boot card. I tried the following (after unmounting the card)::```
sudo mkfs.vfat /medis/disk
```
Terminal says there is no such file or directory.
What am I doing wrong?

---

### Post by 3rdalbum on 2009-07-14
> **RadarBat said:**
> I am trying to format an SDHC flash memory card to vfat so I can use it as a boot card. I tried the following (after unmounting the card)::```
sudo mkfs.vfat /medis/disk
```
Terminal says there is no such file or directory.
What am I doing wrong?

Firstly, there's no "/medis", there's "/media".

Secondly, I believe you need to specify the device file, not the mount point. So it would be SOMETHING like this: sudo mkfs.vfat /dev/sdf

Making sure that /dev/sdf is indeed your SDHC card - you can check with the command:

```
sudo fdisk -l
```

Thirdly, why not just use Gparted?

---

### Post by LowSky on 2009-07-14
gparted could do this for you without the bad spelling...lol


sudo apt-get istall gparted

---

### Post by superprash2003 on 2009-07-15
a small correction , there is a small typo in the command posted above. its 

sudo apt-get install gparted

---

### Post by RadarBat on 2009-07-15
Thank you, gentlepeople for your responses. sorry about the typo, I don't see too well & am not a touch typist.
"sudo fdisk -l" was what I was looking for, and, yes, gparted was much easier. Thanks again.      RB

---

