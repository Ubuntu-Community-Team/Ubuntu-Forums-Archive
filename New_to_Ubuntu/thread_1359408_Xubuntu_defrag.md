---
title: "Xubuntu defrag?"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Gulfvet91 on 2009-12-19
How do you do disk maintenance in xubuntu?   My poor computer hasn't been defragged since I upgraded to 9.10.

---

### Post by snowpine on 2009-12-19
Linux filesystems do not need defragging. It's a Windows thing. :)

---

### Post by coffeecat on 2009-12-19
Don't worry about it. Fragmentation affects all filesystems but is only really significant in Microsoft Filesystems such as FAT32 and NTFS. Ext3 suffers no significant fragmentation until the partition is more than 90% full. Ext4 is even less prone to fragmentation.

Defragging is a Windows pastime. You can forget about it! :)

---

### Post by harrisonk on 2009-12-19
[SIZE=4]Hello

Xubuntu or any *buntu defrags it self automatically.

Harrisonk
[/SIZE]

---

### Post by szymon_g on 2009-12-19
> **snowpine said:**
> Linux filesystems do not need defragging. It's a Windows thing. :)

not true- fragmentation occurs on every filesystem- but on ext3/4 it's much smaller than on fat16/32 or ntfs

---

### Post by snowpine on 2009-12-19
> **szymon_g said:**
> not true- fragmentation occurs on every filesystem- but on ext3/4 it's much smaller than on fat16/32 or ntfs

OK; mind sharing how we can defraggle in that case?

---

### Post by szymon_g on 2009-12-19
> **snowpine said:**
> OK; mind sharing how we can defraggle in that case?

ext2 uses e2defrag, ext4 needs no defragmentation tools (as far i know), ext3 can be defragmented with 
[http://ck.kolivas.org/apps/defrag/defrag-0.07/](http://ck.kolivas.org/apps/defrag/defrag-0.07/) 

you can know the level of fragmentation with fsck.ext3 -nfv (afaik, don't write it from linux, so i cannot check), look for line "non-contiguous inode"

as i wrote- it's fragmentation is much lower than vfat/ntfs, but it exists (on ext2/3) :)

---

### Post by Gulfvet91 on 2009-12-19
Thanks!  That used to be one of my main time wasters on Windows systems.  Take note, Bill Gates!

---

