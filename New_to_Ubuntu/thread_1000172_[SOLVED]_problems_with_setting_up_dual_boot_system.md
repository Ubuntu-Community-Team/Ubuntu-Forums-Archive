---
title: "[SOLVED] problems with setting up dual boot system"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by djyoung4 on 2008-12-02
ok so I tried to set up a dual boot system.  I am already running windows XP and I tried partitioning my drive when I install ubuntu 8.10 but it will not allow me to make enough room for the OS.  It says that I only have 8 megabytes of free space but I know I have about 25 GB.  They are all formatted in NTFS though.  so my question is how do I free up some of that empty space so I can install Ubuntu?  any help would be great.

---

### Post by Idefix82 on 2008-12-02
Are you saying that you have 25 GB free on the Windows partition or is it a separate partition already? If the former, then you need to resize the Windows partition first, then create a new partition in the unallocated space which you have thus freed up.

---

### Post by mapes12 on 2008-12-02
This may help: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Captain_tux on 2008-12-02
Kinda sounds similar to what I went through. Here's my thread... hope it helps!

[http://ubuntuforums.org/showthread.php?t=996303]("http://ubuntuforums.org/showthread.php?t=996303")

---

### Post by djyoung4 on 2008-12-03
yeah I have 25 free GB's inside of my windows partition.  I just want to know how to free that up.  I havent looked at the other advice that people gave me but Ill check it out.  if anybody has any other advice i will take it.  thanks

---

### Post by falcon61102 on 2008-12-03
If you haven't done so already, you probably need to defrag the XP partition a few times to compress everything to the beginning of the drive.  You may have 25 gig of space but if it's not continuous you risk losing data or you can end up with errors like you're getting.

---

### Post by djyoung4 on 2008-12-03
I have defraged a few times but I get the same yellow caution in Gparted that captain tux had.  I think i will defrag a few more times and see what happens.  I wanted to set up 3 partitions that has one windows partition, one ubuntu partition and one partition for my data that is FAT32.  Am i going to have to reformat my harddrive to do that which means it will all get erased.  Or is there a way to just switch it.

---

