---
title: "Partitioning problem."
date: 2010-07-06
forum: New to Ubuntu
---

### Post by numberfive on 2010-07-06
Hi there,  basically I am running Ubuntu 10.04 as the sole OS on this laptop and I would like to resize the primary partition in order to create a new partition and install Windows XP again on that partition.

I have tried to use GParted but it will not let me resize the partition.

In case it matters, I ran the command line:

sudo fdisk -l
And got the following results:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000177a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19098   153397248   83  Linux
/dev/sda2           19098       19458     2890753    5  Extended
/dev/sda5           19098       19458     2890752   82  Linux swap / Solaris


And advice as to how to go around this will be appreciated.

Thanks in advance, Calum

---

### Post by cj.surrusco on 2010-07-06
You can't resize it because it is mounted. You would have to boot into a GParted or Ubuntu live cd and make the changes from there.

---

### Post by Zeike on 2010-07-06
You can't resize the partition while you're using it.  You'll have to boot from a live cd and use gparted from that to do the resize.

---

### Post by warfacegod on 2010-07-06
You must be in a Live environment to resize your Linux partition. An analogy would be standing on a tree branch and cutting through it somewhere between you and the trunk. Nobody can do that and live. Your partition is the same way. Your OS won't survive the resize operation if your in the OS so it won't let you do it. Boot into your Live CD/USB.

---

### Post by numberfive on 2010-07-06
Thanks for the quick replies, will do that now.  :)

---

### Post by garvinrick4 on 2010-07-06
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19098   153397248   83  Linux
/dev/sda2           19098       19458     2890753    5  Extended
/dev/sda5           19098       19458     2890752   82  Linux swap /  Solaris

You have one big partition with Ubuntu and boot in sda1
an Extended partition with swap in it as a logical partition.
Boot into a Live CD.
Can you shrink or resize sda1 from the back side of partition and
leave the front alone with boot in it.  It will come out as unallocated and
then right click on it and make new make a Primary and format as NTFS. Will come out as sda3 or sda4 and has to be Primary. Windows likes sda1 thru sda4 to  reside in.
Install Windows in new partition and then you will have to reinstall  grub from ubuntu install to sda
most likely.

[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

[GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId905459")

---

### Post by Darkness Des on 2010-07-06
Just for reference, Chuck Norris could do that and live.

---

### Post by warfacegod on 2010-07-06
> **Darkness Des said:**
> Just for reference, Chuck Norris could do that and live.

That's a given.

Chuck Norris is the ruler of the world. He just hasn't bothered to tell anyone. His chin alone shakes the pillars of Heaven by its mere existence. 

Chuck Norris could easily stop two taped together turtles.

---

