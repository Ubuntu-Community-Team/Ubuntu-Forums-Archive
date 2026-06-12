---
title: "evil error message. noob here"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by lazdogmc on 2009-03-05
ok so my nerdy brother installed ubuntu. however he isnt nerdy enough to help me with this one..
i got this error message when booting, as far as i can tell its somewhat responsable for me not being able to read my second hard drive.
i know the image isnt the greatest quality but i wasnt about to type the whole thing out... the first line is something like
Boot from [hd0, 2] ext 3     numbers....
[IMG]http://i75.photobucket.com/albums/i306/slaskzoos/05032009327.jpg[/IMG]
any help at all would be greatly apreciated. iv heard great things about the ubuntu community. basically what im hoping to achieve would be ubuntu recognising the hard drive. i have windows xp installed also and it does fine recognising it so im not sure what the problem could be.
thanx in advance.
larry

---

### Post by skymera on 2009-03-05
It looks to be trying to boot from a disk that doesn't exist.
Or it's being pointed in the wrong way.

If it's a new install, just reinstall again, it's the simplest solution and you wont lose much.

---

### Post by lazdogmc on 2009-03-05
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf690f690

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3549    28507311    7  HPFS/NTFS
/dev/sda2            3550        4036     3911827+   7  HPFS/NTFS
/dev/sda3            4037        4644     4883760   83  Linux
/dev/sda4            4645        4705      489982+  82  Linux swap / Solaris

Disk /dev/sdb: 8119 MB, 8119123968 bytes
1 heads, 62 sectors/track, 255768 cylinders
Units = cylinders of 62 * 512 = 31744 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             133      253688     7860224    b  W95 FAT32
Partition 1 does not end on cylinder boundary.


does this explain anything? after a bit of foruming i kinda got the jist that the sdb was my invisable hard drive and still trying to figure out how to make it visable.

---

### Post by lazdogmc on 2009-03-05
actually ignore the sdb thing.. that was my phone.. still not sure how to get this hard drive visable.

---

### Post by skymera on 2009-03-05
How long has Ubuntu been installed?

Try a reinstall, that would give you a fresh start

---

### Post by lazdogmc on 2009-03-06
yeah iv found a way to fix it... buy a new hard drive, it was a rubish hard drive in the first place and wasnt worth the stuffing around. thanx for the help but i think i might just salvage what i need in windows, format it and start over

---

