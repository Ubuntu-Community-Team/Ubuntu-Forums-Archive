---
title: "Re: Partially Unreadable Contents"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by kapad on 2009-07-25
I am having a similar problem
I had resized my partition using gparted and now when I go to properties on filesystem I am shown a very large amount of space as being used and get a message saying that some data is unreadable
can someone help out with this.

```
the output of      Code:
     sudo fdisk -l 
 is 

     Code:
     Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2              15        3277    26209862+  83  Linux
/dev/sda3   *        3278       10926    61440592+   7  HPFS/NTFS
/dev/sda4           10927       30401   156432937+   7  HPFS/NTFS 

```Mod Note: The thread that the OP is talking about is [here]("http://ubuntuforums.org/showthread.php?t=784991").

---

### Post by Sef on 2009-07-26
One problem that I see is that Windows should be on the first primary partition.   That could be part of the problem.

---

### Post by kapad on 2009-07-26
ok. thanx for the reply.
ill try to use gparted to move the partition and see what happens
thnx

---

