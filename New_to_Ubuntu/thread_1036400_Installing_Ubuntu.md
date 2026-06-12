---
title: "Installing Ubuntu"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by rezabrya on 2009-01-10
Hi guys,
      I am very new to ubuntu and this is my first download of it.  I have a 750 gb hdd for my vista install and then i have a 80 gb hdd that i have partitioned into 2 equal partitions.  I am aiming to install ubuntu on one of the partitions so i can have vista as my main os and have ubuntu when i want to use it.  I went to install Ubuntu and i selected the partition and when i clicked forward it said something along the line of "no root folder, change this in the partition menu".  No matter what id o it come sup with this error.  it ried deleting the partition and then remaki9ng it inside Ubuntu but that didnt work.  I formatted and that didnt work.  It is a ntfs partition and it is 33 gb so it should be good.  what am i doing wrong?

---

### Post by taurus on 2009-01-10
You can use gparted from the LiveCD (System -> Administration) and divide that 33GB partition into two partitions: / (31GB) & swap (2GB).  Format the first partition as ext3 and the swap (smaller one) as swap.  Then, run the installer.  When you get to the partition screen, pick the Manual option and make sure you tell the installer to mount the 31GB partition to /.  The installer should know how to handle the swap partition on it own.

---

### Post by JoshuaRL on 2009-01-10
Well, first off welcome to Ubuntu!

If you want to install Ubuntu you should install it on a ext3 filesystem partition.  That's the partition Ubuntu uses.  Second, you'll need to set a mount point.  In the partitioner, that's what you/re looking for.  In the partition you want Ubuntu in, put the following in the mount point field:
```

/

```
Also, if you want access to your Vista partition or any other partitions you have, you'll need to designate a mount point for them too.  I would suggest something like:
```

/media/Vista (or some name you want that folder/partition named in Ubuntu)

```
You'll need to do that for each partition you want mounted.  Does that help?

---

