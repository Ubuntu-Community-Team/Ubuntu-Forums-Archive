---
title: "partition magic destroyed my Virtual disk in virtualbox"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by medya on 2010-01-22
hey guys

I had windows 7 as guest on my ubuntu 9.10
on virtualbox,
I had a 20 GB of virtual disk, VDI

then I mounted this partition magic 8 bootable CD, to try it

it told me BAD partition, and asked me if it can fix it for me , I said fine fix it,
then it restarted, 
now when I start it , it says
> a disk read error occurred
press ctrl+alt+del to restart 

---

### Post by JiuJitsu500 on 2010-01-22
Is it saying that only when you try to load your Win7 in virtualbox or your computer?

As far as I know, partitioning tools most times that can recognise virtual disks will read them as bad and make their best attempts to "fix" them by re-formatting that part to a linux (journaling) format, i.e. EXT2, EXT4, etc...

Or it will completely remove them. I could be wrong, but it happened to me before with Windows XP and I had to delete the partition from the virtual media manager in virtualbox and re-install windows. Sucks.... I'm not sure if it's possible to recover them unless you can reformat your virtual disk to NTFS I believe (but don't quote me on that) or whatever the windows partitions are normally formatted in.

Mine like I said didn't work though and I had to reinstall and lose the Zune, Star Downloader (best free download tool ever), registry cleaner, all that crap windows needs...

---

### Post by medya on 2010-01-22
guys I fixed it , to hell with Partition magic that shows my partion as Bad !!!
gparted fixed it !

thank you gparted :X KISSS

---

### Post by JiuJitsu500 on 2010-01-22
Sweet.... GParted is the way to go :) I hear people with problems in Partition Magic often enough to just avoid it....

---

