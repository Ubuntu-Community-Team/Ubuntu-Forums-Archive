---
title: "Ok to delete extended partition?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Rumpletumbler on 2010-08-23
I chose the use all available disk space when I installed Lucid and didn't pay any attention to the partitions created at the time.

Down the road I wanted to encrypt the swap so I followed this for the swap file:

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

Turns out sometimes it mounts and sometimes not.

If I look at disk manager I have two 1.9GB partitions. One swap and one extended. The extended only has a delete or format option. I was thinking this could be the old swap or something created during the install that evidently isn't being used. 

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60569   486518784   83  Linux
/dev/sda2           60570       60802     1865729    5  Extended
/dev/sda5           60570       60802     1865728   82  Linux swap / SolarisCan I just delete the extended partition without harm?

---

### Post by QLee on 2010-08-23
[QUOTE=Rumpletumbler]
If I look at disk manager I have two 1.9GB partitions. One swap and one extended. The extended only has a delete or format option. I was thinking this could be the old swap or something created during the install that evidently isn't being used. 

Can I just delete the extended partition without harm?[/QUOTE]

Maybe, if you have sufficient RAM your system could run without swap.

Because that's what you would be doing, eliminating your swap. You don't have two partitions, the extended partition 2 is a container for logical partition 5.

---

### Post by mcduck on 2010-08-23
The swap (dev/sda5) is *inside* the extended partition. Don't delete the extended partition or you'll lose both partitions.

The MBR partition tables are originally only able to support 4 primary partitions. To allow for more complex partition layouts one of these partitions is replaced by an extended partition, which serves as a "container" allowing you to add even more partitions (logical partitions).

Ubuntu's installer by default creates an extended partition and puts swap inside it even if you aren't creating more than 4 partitions on your disk. This gives you more flexibility if you need to edit your partitions at a later time.

---

### Post by Rumpletumbler on 2010-08-23
Thank you. The more I learn the dumber I feel. haha.

---

