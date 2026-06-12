---
title: "partition problems"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Festerbaun on 2009-12-31
ronin@ronin-rogue:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        5249    42117128    7  HPFS/NTFS
/dev/sda3            5250       18183   103892355    5  Extended
/dev/sda4           18184       19457    10233405   db  CP/M / CTOS / ...
/dev/sda5            5250        6567    10586803+  83  Linux
/dev/sda6           17766       18183     3357553+  82  Linux swap / Solaris
/dev/sda7            6568       17394    86967846   83  Linux
/dev/sda8           17395       17765     2980026   82  Linux swap / Solaris

Can someone please explain this?  I would like to clean up unused partitions but have had pretty bad results trying so far.

---

### Post by Chris Edgell on 2009-12-31
I thought I'd send this along. It may be stuff everybody already knows but me, in which case please disregard.


PARTITIONS     JKyleOKC

Think of your hard drive as a big box that has a number of smaller boxes in it (the partitions). Its name is "sda" and the file system addresses it as "/dev/sda" without a number. The partitions are numbered: sda1 and so on, and addressed as "/dev/sda1" et cetera.

The letters (a, b, c, d) are assigned according to the connectors on the motherboard and the numbers according to the sequence of entries in the drive's partition table (an area at the start of the drive that tells where the data is located). This table has room for only four entries, which will be sda1 through sda4. To get more partitions, one of the four has to be an "extended" partition, which is another box full of partitions such as your sda5, 6, 7, and 8. You don't need to worry about these because the partition manager will take care of the details.

To access the contents of a partition, it has to be mounted. The file manager of the live CD normally does this for you, so that you can click on the partition's icon and see the list of directories it contains. One of them will be "home" and inside that directory will be at least one more, bearing your user name. That inner directory is the one you want to back up.

If the file manager does not show you icons for the partitions, you'll need to "mount" them to gain access. However let's not try to cross that bridge until it becomes necessary, since it can be a bit confusing at first! Tools are available to simplify it, fortunately.

With a little experience you'll find this stuff much easier to get along with; it's all pretty logical, just different from the systems that you're used to!

				....................................

---

### Post by Captain_tux on 2009-12-31
Do you have more than one Linux distro installed?

A program like GParted can be used to get rid of un-needed partitions...

---

### Post by Festerbaun on 2009-12-31
I do not have multi versions of linux installed just one or two extra ubuntu installs.  And thanks to the first poster that was unkown info to me.   I tried to delete the extra installs but when I do my system crashes and I'm booting up to a grub rescue prompt.  I got around this by installing ubuntu again because I could not boot into either os (much to my wife's dismay, she loves to use this netbook).  So to keep us both happy I did a dual boot.  I have read that there is no need for dual boot these days but it did offer a quick and painless install for a extremely inexperienced linux user/crasher.  
 
I would love to SAFELY get rid of these partitions and reclaim my extra space, I just do not have the know how to do so.  Any suggestions/help will be appreciated.

---

### Post by bodhi.zazen on 2009-12-31
Well, before you go deleting partitions you need to know what is in each partition.

For basic information on partitioning see : 

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 


In terms of deleting partitions and booting, your system boots with "grub" and the files are in your boot partition. You need to re-install grub if you remove the partition you boot from.

See : 

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

That thread is for grub 1 , but covers the basics.

For info on grub 2 (Ubuntu 9.10) see:

[Grub 2 - Ubuntu Wiki]("https://wiki.ubuntu.com/Grub2")

---

