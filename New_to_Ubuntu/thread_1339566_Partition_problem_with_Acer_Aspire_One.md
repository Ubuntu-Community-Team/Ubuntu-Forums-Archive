---
title: "Partition problem with Acer Aspire One"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Prince Valiant on 2009-11-27
Hello,

I'm having trouble with Grub on my Acer Aspire One D250.  I've installed Ubuntu Netbook Remix 9.10 next to Windows XP and a Windows Vista bootloader.  Due to install problems (to put it simply) I installed Ubuntu 3 times next to each other.  (I wanted to keep Windows on there and couldn't find a way to simply replace one OS.)  However, when I tried to delete one of the sda partitions for a previous Ubuntu install, an error came up, and when I next restarted my computer, Grub said "no such partition."

I can't even access Windows.  What partition should I create so that Windows works and I can install UNR?  I can run the Acer off a flash drive UNR, so the hard drive can be accessed.  Any help would be greatly appreciated.

Let me know what further info I should supply.  Thanks in advance!

-Val

---

### Post by Prince Valiant on 2009-11-28
Well, I fixed it.

In the end, I used a combination of GParted, Palimpsest, and perseverance to delete all but the original Windows partitions (Acer and PQService) into one big unallocated space.  I did a fresh install of Ubuntu into that (after formatting it into ext2), and left 15 GB of the ext2 as an extra 'storage' partition.  The Windows OS was saved, and Ubuntu works great.  :-D

-Val

---

