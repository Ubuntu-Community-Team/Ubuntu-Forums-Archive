---
title: "Grub boot error&gt;_ and a whole lot worse"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by VraiChevalier on 2010-07-18
Acer Aspire One, Intel Atom N280, 2GB RAM, 160GB HDD, dual booting Windows 7 Starter and Ubuntu 10.04 Netbook edition. Recently I decided to install the LXDE desktop and try it out. Not liking that I then decided to try the KDE Plasma desktop. Everything seemed to install OK. I logged out and back in several times with no problems.

The next day when I booted the machine I was greeted with the dreaded Grub2 "grub error" boot prompt. No worries I thought, as I found a number of tutorials on how to fix this. And that's when it gets a whole lot worse; although entering "ls" at the grub error prompt lists my partitions, when I look at the disk layout from G-Parted it shows my Ubuntu partition as "unallocated"!

I am not able to read any data on the Ubuntu partition as it does not show up when I boot any Live disks. I recently read something where a person was able to rebuild their file table, using fdisk I think. Does anyone know if such a thing is possible? Any way to rebuild or restore the file table? Apparently the partitions are still there. Can I post more info which will help or clarify?

---

### Post by cariboo on 2010-07-18
Try running:

```
sudo fsck -y /dev/sdX
```

from the Live CD, where /dev/sdX is your Ubuntu partition.

---

### Post by VraiChevalier on 2010-07-18
Thanks Cariboo907, I'll try that. I am researching the file system now. One other odd thing I forgot to mention is that the Windows partitions show up and I can see the data on them. It is just the Ubuntu partition which does not show up as mountable. I'll try running the fsck now.

---

