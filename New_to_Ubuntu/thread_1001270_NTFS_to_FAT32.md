---
title: "NTFS to FAT32"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by djyoung4 on 2008-12-03
Ok so i want to partition my drive so that Windows is in one partition, Ubuntu in another and then all my data is in a third.  The only problem is that my harddrive right now is formatted in NTFS but in order for both OS's to access the drive it needs to be in FAT32.  my question is will I have to wipe the whole disk to format it in FAT32 or can I convert it somehow.  any advice on how to set up the partitions would be helpful too.

---

### Post by dizee on 2008-12-03
Ubuntu has full read & write support for NTFS since Feisty. So it wouldn't really be worth the hassle.

---

### Post by sdowney717 on 2008-12-03
You can also get windows to read linux ext2 and ext3 partitions using IFS drives.
[http://www.fs-driver.org/](http://www.fs-driver.org/)
SO, you can go both ways with XP and linux.

---

### Post by louieb on 2008-12-03
> **dizee said:**
> Ubuntu has full read & write support for NTFS since Feisty. So it wouldn't really be worth the hassle.
+1  fat out,  ext3 or NTFS for data in.

Which version of windows. Vista can shrink itself (recommend). Gparted can shrink an NTFS partition. Then you can use the unallocated space to create additional  partitions however you want.  Some of the partition layout I have used: [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by evilkastel on 2008-12-03
> Ubuntu has full read & write support for NTFS since Feisty. So it wouldn't really be worth the hassle. 

MMm... i wouldn't say so. YOu know, if you want to make the drive FAT you will have to wipe the disc. Ubuntu,can read NTFS quite well yet Writing is not encouraged. Support is there, but you should avoid writing NTFS from ubuntu if there is a choice.
 The ext driver works, but also is not recommended for writing, so you should chosse what OS will you run mainly and format according, and if your drive is not too big and you think you will use them bought equally, then go FAT.

---

### Post by djyoung4 on 2008-12-03
ok so the tutorial that I read on how to set up a dual boot system said that Ubuntu couldn't read or write to FAT so i am good on that then.  I am running xp and have been having some problems with setting up a dual boot.  Gparted will not allow me to partition the drive and it has a yellow caution symbol next to the drive when I do open gparted.  louieb thanks for that link.  that helps.  One other question I have is if I shrink my Windows partition and all of my data is in my windows partition will ubuntu be able to read that data say for instance I have some music in my windows partition will i be able to play it in Ubuntu?

---

### Post by egalvan on 2008-12-03
> **evilkastel said:**
> MMm... i wouldn't say so. YOu know, if you want to make the drive FAT you will have to wipe the disc. Ubuntu,can read NTFS quite well yet Writing is not encouraged. Support is there, but you should avoid writing NTFS from ubuntu if there is a choice.
 The ext driver works, but also is not recommended for writing, so you should chosse what OS will you run mainly and format according, and if your drive is not too big and you think you will use them bought equally, then go FAT.

Nine different machines dual-booting...

running NTFS with Ubuntu since 8.04
and ext2/3 with XP since the same.

No problems found yet.

ErnestG

---

### Post by kwilliam on 2008-12-03
> **djyoung4 said:**
> One other question I have is if I shrink my Windows partition and all of my data is in my windows partition will ubuntu be able to read that data say for instance I have some music in my windows partition will i be able to play it in Ubuntu?

I do that all the time. Once the NTFS partition is mounted in Ubuntu, it's just like any other hard disk or flash drive. E.g., my XP partition is mounted at boot, so I can just browse to /media/XP/Documents and Settings/<User>/My Documents/.....

---

### Post by Tatty on 2008-12-03
> **evilkastel said:**
> Ubuntu,can read NTFS quite well yet Writing is not encouraged. Support is there, but you should avoid writing NTFS from ubuntu if there is a choice.

I would disagree with that.  NTFS support in linux has been very mature for a long time now and i would say the inherent benefits of having an NTFS drive will by far outweigh the slightly increased chance of write failure than you would have with a FAT32 drive.

---

### Post by djyoung4 on 2008-12-03
thanks everybody for your help.  I am gonna back everything up and try to install.  I finally defrag and CHKDSK enough times where I was able to make Gparted allow me to partition my disk.  thanks for all your help again

---

