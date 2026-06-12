---
title: "reinstall"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by drmi115 on 2009-03-20
I messed some things up in the audio portion of ubuntu and need to reinstall in a way that starts over completely.  I just want to save my windows partition.  This is what I have right now.  What do I save and discard?  How do I do it?

1dev/sda 1 ------ c  W95 FAT32 (LBA)
1dev/sda 2 ------ f  W95 FAT32 (LBA)
1dev/sda 5 ------ 7  HPFS/NTFS
1dev/sda 6 ------ 7  HPFS/NTFS
1dev/sda 7 ------ 7  HPFS/NTFS
1dev/sda 8 ------ 83 Linux
1dev/sda 9 ------ 82 Linux swap / Solaris
1dev/sda 10 ----- 83 Linux 
1dev/sda 11 ----- 82 Linux swap / Solaris

Thanks in advance from a novice

---

### Post by ivanvajar on 2009-03-20
Well, you can format whatever partition you want from LiveCD (your Ubuntu installation CD), just don't do anything to your Windows partition. Also, you can run installation and format desired partition from manual preparation of partitions.

I don't understand why there are 2 Linux and 2 swap partitions. Even if you have more than 1 Linux installed, they need only 1 swap. You can merge those partitions by deleting sda 9,10 and 11 and then resizing sda 8. After that, you just need to create swap that is as big as your RAM.

---

### Post by drmi115 on 2009-03-20
So, I assume I adjust the partitions manually, and there will be a format option.  Is that correct?  Is there also a delete option or merge option?

I also don't understand why there are two Ubuntu partitions.  I only installed once, but I always have two options when I boot up my system.  I had three equal partitions when I installed the first time, and I let the installer adjust the partitions.

---

