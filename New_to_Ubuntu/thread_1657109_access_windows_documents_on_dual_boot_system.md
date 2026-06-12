---
title: "access windows documents on dual boot system"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Zoomy on 2010-12-31
I have a dual booting system, Windows 7 and Ubuntu.  How would I get to my music and photos on my windows partition?

---

### Post by laithbsoul on 2011-01-01
you should see your windows partition under Places click on it and it will mount then go to where the files your looking for are located in the partition. as simple as that.

---

### Post by muuwt1 on 2011-01-01
do you have the mount loader program from panel? if not add that to panel and i always thought that made things alot clearer.

also, type in terminal
fdisk -l or parted -l
and see what that looks like. look for how big the filesystems are and see if everything adds up. look where they are located. /dev/blahblahblah

your windows partition may be ntfs and you might need some ntfs config tool or whatever. cross that bridge when you get there. good luck

---

