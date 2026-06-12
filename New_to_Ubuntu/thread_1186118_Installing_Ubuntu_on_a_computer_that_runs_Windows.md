---
title: "Installing Ubuntu on a computer that runs Windows"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by gabriel_s on 2009-06-13
Hi, i plan to buy a new laptop and i would like to work with both Ubuntu and Windows (dual boot). This is something i have done in the past, but always i was the one who installed both Windows and Linux, and i created the partitions during the installation. The problem is that most laptops here come with Windows already installed, and you don't get a CD. My question is - if i get a laptop with Windows installed ( on the entire drive ), create a partition in Windows using a partitioning software ( like Partition Magic ), can i install Ubuntu on that partition? i once read an article saying that Linux must use the first 1024 blocks of the hard drive, but it was a very old article.

Thanks.

---

### Post by prvteprts on 2009-06-13
Yes. Before creating a new partition though, create a backup disc for your Windows installation. For the resizing and creation of the new partition, you can use Vista's partitioner if that is the preinstalled OS (XP doesn't have a built in). Or you could also use GParted LiveCD. You can install Ubuntu on the new partition, and it will take care of the boot setup.

---

