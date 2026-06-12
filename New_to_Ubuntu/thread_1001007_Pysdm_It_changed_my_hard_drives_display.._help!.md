---
title: "Pysdm: It changed my hard drives display.. help!"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by DJMattB241 on 2008-12-03
I installed pysdm in an effort to get my new third internal hard drive to automount on bootup. For some reason it wasn't doing it automatically, and I couldn't remember how I did it with my first extra hard drive. So after some googling, I found pysdm.

Anyways, everything is working great now except one thing: my primary hard drive now shows up on my desktop as "98.5gb Media" which is very strange, since that's not its name.

Pysdm also now lists it as an NTFS drive, which it also is not, its ext3. What's weird is, my extra hard drive is named Media, but now so is my primary drive.

Here's what pysdm lists:
sda1 (this is my boot drive)
Name: Media
Mountpoint: /media/Media
Type: ntfs-3g

sda5 (swap partition)
Name: sda5
Mountpoint: /media/sda5
Type: swap

sdb1 (this is my older media drive)
Name: Media
Mountpoint: /media/Media
Type: ntfs-3g

sdc1 (this is my new media drive)
Name: Media2
Mountpoint: /media/Media2
Type: ntfs

Can anyone provide help as to why this might be happening and how I could fix it? Thanks!

---

### Post by DJMattB241 on 2008-12-03
bump. :(

---

