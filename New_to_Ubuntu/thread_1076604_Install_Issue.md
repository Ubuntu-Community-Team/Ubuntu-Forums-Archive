---
title: "Install Issue"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by F4r4Zm0In on 2009-02-21
Hey all,

I am running ubuntu 8.10 

The results of my fdisk -l are as follows:

> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc791c791

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4785    38435481   83  Linux
/dev/sda2            4786        4865      642600    5  Extended
/dev/sda5            4786        4865      642568+  82  Linux swap / Solaris


Now, the thing is i am looking to install another OS lets say bt3 final

I know that out of my 40.0 GB space, More than 38.5 Gb is already occupied by /dev/sda1 in which ubuntu is installed 

I need to know in which partition should i go with the bt3 final installation, or should i create a new partition, if so please tell me how to create a partition without affecting my current ubuntu functionality

Regards

---

### Post by shredder12 on 2009-02-21
well,, you can probably shrink the ubuntu's partition using gparted..
but take my advice and be really careful while doing it..
i think that doing this might cause a problem with the current installed version.. but probably reading gparted's manual will help you out..

---

### Post by F4r4Zm0In on 2009-02-21
Thanks for the info will search for gparted tut and then revert back

Edit: Just read out that we need to unmount the partition first in order to resize it

But, i don't think that i can do this, because this partition is the only one i have and its in use by ubuntu

Stucked!

---

