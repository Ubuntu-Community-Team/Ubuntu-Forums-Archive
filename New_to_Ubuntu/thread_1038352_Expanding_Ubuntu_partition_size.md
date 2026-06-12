---
title: "Expanding Ubuntu partition size"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by mark_j on 2009-01-12
My computer has 2 physical 250GB SATA hard drives.  Disk 1 has two approx 120GB partitions (C: & D:) and Disk 2 was orginally unpartitioned.

I installed Ubuntu 8.10 to Disk 2 (dual boot) and created a 50GB partition for it to use during the install process.  I love using Ubuntu.  A lot.  I am now installing my vast library of ID Software shooters, etc. and am having a blast.  It reminds me of why I became a computer hobbyist years ago.

Anyway, here is the problem.  I want Ubuntu to have more than 50GB of my second HDD.  In fact, I want it to have the whole darn thing.  What is the best way to make that happen?  

Thanks

---

### Post by kansasnoob on 2009-01-12
Boot your Ubuntu live CD. Go to System > Administration > Partition Editor, and of course be sure what drive and what partition you're working with, and you'll have to click on the SWAP and select "swapoff", then you should be able to resize, delete, etc.

Look:

[ATTACH]99660[/ATTACH]

You see in the somewhat upper right hand corner you can "toggle" from drive to drive (that is sda, sdb, etc.)

And of course sda is drive #1, sdb is drive #2, etc.

I should also warn you that resizing or moving the SWAP will result in UUID problems that can be easily straightened out.

You'll know you have UUID problems if SWAP no longer works or if you lose the nice "quiet" Usplash.

---

