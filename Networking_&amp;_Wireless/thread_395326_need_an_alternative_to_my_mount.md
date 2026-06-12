---
title: "need an alternative to my mount"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by thegrimgod on 2007-03-28
i dont know if i mounted correctly but i need a solution for my pc and networking.Currently my second hard drive is mounted in fstab with /dev/hdd1 /media/hdd1 ext3 defaults 0 0  but after about 30 reboots i believe , it does some check warning me that i mounted it without checking or something, more then 30 times...but all works i suppose , i just need to solve that
and for my network i mount like this //myserver/share /media/myserver/share smbfs credentials=/home/grim/smbpass 0 0
//myserver/share2 /media/myserver/share2 smbfs credentials=/home/grim/smbpass 0 0 which are basicly 2 hard drives on a separate pc , that i use for storage , its a windows machine , and i have many other windows machines that i mount some times , that one is always on...so i dont check much. but my problem is that i have  a lot of music on another windows pc , and if i mount my music folder from that pc to lets say an empty folder /home/grim/Desktop/d , as soon as somebody shuts down that pc , my folder is ruined , it doesnt unmount or somethin ,but i cant even acces that folder...so is there a solution to networking other than mounting to read/write?

---

### Post by lloyd_b on 2007-03-28
>  i dont know if i mounted correctly but i need a solution for my pc and networking.Currently my second hard drive is mounted in fstab with /dev/hdd1 /media/hdd1 ext3 defaults 0 0 but after about 30 reboots i believe , it does some check warning me that i mounted it without checking or something, more then 30 times...but all works i suppose , i just need to solve that

There's nothing wrong.  By default, each drive is assigned a maximum number of mounts.  When this count is reached, the system does a "fsck" (filesystem check) to make sure no errors have crept in.

You can change this by running the "tune2fs" command in a terminal window:
```
sudo tune2fs -c {number} {device}
```
where {number} is the maximum number of mounts before a check is forced (set it to 0 to disable these checks, though this is not recommended), and {device} is the entry from shown by "df" (such as "/dev/hdd1").

Lloyd B.

---

### Post by thegrimgod on 2007-03-28
ty for reply lloyd ,now i udnerstand what goin on with that hard drive ,but what do i have to do with my networking, any solution to that?

---

