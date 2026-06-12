---
title: "lvm : basic questions and data safety"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by beopen on 2011-01-18
i have the following questions on LVM

1.When u create a lvm from multiple disks, since the Volume group in such case is composed of physical volumes from different disks, what happens if one of the disk fails physically. I read somewhere on the net that in that case the whole Volume group goes bust. As an eg suppose from two 160gb drives i create a 80gb LVM [taking 40gb from each drive] and one of the disks goes bust; in that case would the entire 80gb will go bust.  Or some part will be recoverable?
2. What all partitions should be outside the LVM. One i read was /boot. Balance there are multiple views. One says '/' should be out[risky to keep 'root' inside lvm, if anything happens to root , then the whole lvm will go bust] one says swap should be out and vice-versa. Is there any official documentation of any linux on the same. Pls give me a practical view of what should be and should not. Also the official documentation links if any please paste the link
3. how do we know on which hdd what is stored under LVM when using multiple disks? eg i suppose create '/' home and swap partitions  using 2 disks. Which partition is stored in which disk?
4.Does power failure problems cause LVM to go bust more fast than non-lvm systems. In general i know the same is bad for either case, yet i read on net many writing -ve for lvm based systems of power failure.
5. Any specific file system to be used with LVM logical partitions. Or say ext4 is enough.
6.For /boot is only ext2 to be used or can i use ext4 also. And how much space is really needed for this partition. The range goes from 100-500mb. With some info on net saying should not be more than 100mb. I plan to run only one distro. Pls suggest the space for the same for installing ubuntu 10.04
7. Is shrinking of a logical volume under a lvm is risky or results in data loss. I just found one article on the net where it was written "Shrinking a logical volume is hazardous." link:[http://www.linuxbsdos.com/2008/09/24/the-benefits-of-using-linux-logical-volume-manager/](http://www.linuxbsdos.com/2008/09/24/the-benefits-of-using-linux-logical-volume-manager/)
This article is of 2008 . So here it suggest to allocate only that much as required by the system and one can easily expand later. Is this point valid even now?
8.What does lvm snapshot really does? I did not understand the technical answers. One answer was though seems simple still went over board. "LVM snapshots are meant to capture the filesystem in a frozen state. They are not meant to be a backup in and of themselves. They are, however, useful for obtaining backup images that are consistent because the frozen image cannot and will not change during the backup process. So while you won't use them directly to make long-term backups, they will be of great value in any backup process that you decide to use. [http://serverfault.com/questions/23965/lvm-snapshots-as-a-backup-strategy](http://serverfault.com/questions/23965/lvm-snapshots-as-a-backup-strategy)
Some compare it with system restore of windows. Typically i never understood that also. And during pc crash i had to use crude method to get my system back and system restore was a failure and i never enabled it thereafter.
So i would like an explanation in simple terms of what that whole thing is.

9.Is LVM now a stable release. The info on net is of multiple periods. So what is the current state. I mean is it calm and quite for a typical normal home use, where not much of a fiddling is done.

Would highly appreciate answers for the same.

regards

---

### Post by oldfred on 2011-01-18
I do not use LVM. Some info here:

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

