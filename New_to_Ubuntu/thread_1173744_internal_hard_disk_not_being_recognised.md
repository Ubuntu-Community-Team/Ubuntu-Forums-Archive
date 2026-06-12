---
title: "internal hard disk not being recognised"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by kunalhbs on 2009-05-30
i have a 64 bit vista on a HP machine..
i installed ubuntu 9.04 along with vista..
i am not being able to view the c drive or the d drive..
i have installed ubuntu inside windows
only the external hard disk and the cd rom drives are visible..
is this because of 64 bit architecture or some other hardware issues..

config..
vista home premium 64 bit
4 GB RAM.
Intel Core 2 duo T5800

---

### Post by kunalhbs on 2009-05-30
kunal@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x19814382

   Device Boot        Start           End         Blocks             Id    System
/dev/sda1   *              1             30743    232414176+     7    HPFS/NTFS
/dev/sda2                30743       32301     11781120       7     HPFS/NTFS


searched this in another forum..got upto dis point..
my hard disk is being recognised..
but it is not showed under the Places tab.
wat to do next...

---

### Post by QIII on 2009-05-30
When you click Places, do you see any icons labeled something like "250 GB Media"?

---

### Post by QIII on 2009-05-30
When you click Places, do you see any icons labeled something like 250 GB Media?

---

### Post by kunalhbs on 2009-05-30
no..
it jus shows file system..
but under dat there is no mention of the drives..
as i said earllier only external hdd and cd rom drives are visible..
any way to get the internal drives listed on the desktop or under the Places tab..??

---

