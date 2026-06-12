---
title: "how can mount &quot;C&quot; from windows?"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by raafaell on 2008-02-08
hey guys, i'm having a little problem with Gutsy, while ago was all normal, but now, i can't import mp3's from the other partition "C", how could I just try to import/mount it again..



----
a while ago my computer started to upload as I started to, and an error has occurred..
Thx for any help.

---

### Post by jakommo on 2008-02-08
Hi,

try
```
 sudo mount /dev/sda1 /mnt
```
where /dev/sda1 is the first partiton on your first (SATA)drive and /mnt ist the point where you want it mounted.
depending on your setup this could vary. e.g. if you have a IDE drive it could be /dev/hda1

you can check it by running
```
sudo fdisk -l /dev/sda or hda
```
and see which partition is NTFS or FAT

---

### Post by raafaell on 2008-02-09
> **jakommo said:**
> Hi,

try
```
 sudo mount /dev/sda1 /mnt
```
where /dev/sda1 is the first partiton on your first (SATA)drive and /mnt ist the point where you want it mounted.
depending on your setup this could vary. e.g. if you have a IDE drive it could be /dev/hda1

you can check it by running
```
sudo fdisk -l /dev/sda or hda
```
and see which partition is NTFS or FAT

thanks. :D

---

