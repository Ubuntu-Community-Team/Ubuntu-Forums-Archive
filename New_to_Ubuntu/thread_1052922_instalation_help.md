---
title: "instalation help"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by shugs on 2009-01-28
hello,

I am upgrading my ubuntu to 8.10

However the partitioner has got me a little confused.

The computer currently has windows vista and Ubuntu 8.10 as a dual boot. When installing 8.10 the partitioner does not seem to give me the option to install 8.10 on the existing 8.04 partition (i.e. formatting the 8.04 partition and installing 8.10 on it) however only seems to give me the option to either create yet another partition or use 'guided' the entire disk.

Do I use the third 'manual' option? I have had a look around at guides which say that 'manual' should only be used when there are no OS' on the hard drive.

Help is much appreciated!

---

### Post by Elfy on 2009-01-28
yep use manual - you'll then see your linux partitions, you can safely ignore the swap - but select partition 8.04 is installed to - then Edit partition - you want to pick a type in Use As - ext3 is default, then make sure format is ticked. Pick / from the Mountpoint box

---

### Post by shugs on 2009-01-28
Awesome, thanks for the speedy reply..

---

