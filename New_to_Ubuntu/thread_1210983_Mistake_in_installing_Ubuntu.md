---
title: "Mistake in installing Ubuntu"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Tender Prey on 2009-07-12
Hallo to everybody,
i'm very new to ubuntu.
Yesterday i installed Ubunto on my PC with a dual boot installation, unfortunately i committed a mistake in installing since a create a very small partition reserved to ubuntu (just 2.5 giga!!!!). There exist a way to expand this partition (reducing then the partition reserved to windows)?
Thanks to all.
Regards

Stefano

---

### Post by ~sHyLoCk~ on 2009-07-12
If you want to resize your partition, [gparted]("http://maketecheasier.com/resize-create-partitions-with-gnome-partition-editor-gparted/2009/01/06") might help you.

---

### Post by Tender Prey on 2009-07-12
Many thanks!!
Regards.

---

### Post by Gone fishing on 2009-07-12
Yes

You can use a gparted CD but this is also on the live CD. I would suggest that you start on the live CD. Delete the small linux partition the resize the Windows (ntfs) partition. Then reinstall and when the partitioning window appears choose manual and create three partitions one for / one for /home and finally a small swap partition not smaller that 500meg and not larger than X2 RAM.

---

### Post by Tender Prey on 2009-07-12
Hi,

i repeat just to be sure i undestrood what you told me.
I insert the cd (where i have the iso), then i delete my already installed linux, then i restart the installation creating 3 partitions. But...when i installed Ubuntu i didn't find a way to create 3 partitions...

---

### Post by 3rdalbum on 2009-07-12
> **Tender Prey said:**
> Hi,

i repeat just to be sure i undestrood what you told me.
I insert the cd (where i have the iso), then i delete my already installed linux, then i restart the installation creating 3 partitions. But...when i installed Ubuntu i didn't find a way to create 3 partitions...

You need to use the "Manual" partitioning option to make 3 partitions. Since you're new to Ubuntu I still think you should use the regular, easy partitioner (the same one you used before), but of course this time remember to move the slider towards the left so you have a bigger partition :-)

---

### Post by Tender Prey on 2009-07-12
:p

Thanks....this time i hope i won't do disaster!!!!

---

