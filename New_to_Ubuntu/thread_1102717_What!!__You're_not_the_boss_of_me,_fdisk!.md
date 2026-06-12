---
title: "What?!!?  You're not the boss of me, fdisk!"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by DigiTan on 2009-03-21
I made some extra partitions so I could do my Ubuntu install.  I need the same thing to add openSUSE, but fdisk won't let me make another extended partition.  Should I just tear down the original extended partition and make a bigger one?

---

### Post by taurus on 2009-03-21
Fdisk only displays your partition table.  If you want to create a partition from a terminal, use cfdisk.

---

### Post by cholericfun on 2009-03-21
correct me if i'm wrong but ...
you cant just partition around as you please,
4 is max
after that you may be able to play about with logicals (no idea)

PS
use gparted on the Live CD (system/applications) to mess around with the HD

---

### Post by DigiTan on 2009-03-22
> **taurus said:**
> Fdisk only displays your partition table.  If you want to create a partition from a terminal, use cfdisk.

Uh-oh.  You might wanna tell that to my fdisk copy because that's what I used to partition all of my Ubuntu space.  FDisk even boosted my Windows partition.

Here's the output I forgot to mention.  I made an extended partition (/sda2) to host logical partitions for my Ubuntu /, /home, and swapspace.  Now I want / and /home space for openSUSE, but I get the "You cannot change a partition into an extended one or vice versa" lecture.  I could of course delete sda2 and rebuild it as a bigger, badder partition, but I need to know if that will cause data loss.

```
green@green-desktop:~$ sudo fdisk /dev/sda
[sudo] password for green: 

The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa89b82a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30820   247561618+   7  HPFS/NTFS
/dev/sda2           30821       34867    32507527+   5  Extended
/dev/sda5           30821       31992     9414058+  83  Linux
/dev/sda6           31993       34604    20980858+  83  Linux
/dev/sda7           34605       34867     2112516   82  Linux swap / Solaris

Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Partition number (1-4): 3
First cylinder (34868-38913, default 34868): 
Using default value 34868
Last cylinder or +size or +sizeM or +sizeK (34868-38913, default 38913): 38781

Command (m for help): t
Partition number (1-7): 3
Hex code (type L to list codes): 5
You cannot change a partition into an extended one or vice versa
Delete it first.
```

---

### Post by cholericfun on 2009-03-22
partition : data loss = certain
looks like you've got as many partitions as can be already so *maybe* you could do logical partitions to workaround...

---

### Post by gali98 on 2009-03-22
> **DigiTan said:**
> Uh-oh.  You might wanna tell that to my fdisk copy because that's what I used to partition all of my Ubuntu space.  FDisk even boosted my Windows partition.

Hahaha!!!! but seriously cfdisk is a lot easier to work with...
Like some people have said, you can only have 4 primary partitions. You will need to delete one and repartition it as a logical partition which you can then partion something like 16 more times... (it may just be 4)
Just make sure you back up all your data.
Deleting a partion will delete (well to get into technicalities, its still there, but it won't be easy to get to... for all real purposes its gone...)
all the data in that partition... Changing a disk label will delete everything on the disk. I also wouldn't suggest just partitioning for fun :) your data gets a little scared when you do that. 
I think your best bet (if possible) would be to repartion your current swap partition as logical and go from there.. resizing as needed.
Kory

---

### Post by Locutus_of_Borg on 2009-03-22
you can only have 4 primary partitions, an extended partition counts as a primary, and you can only have one extended partition

fdisk does in fact create partitions to whomever suggested it doesnt

---

### Post by egalvan on 2009-03-22
> **DigiTan said:**
> 

   Device Boot      Start         End      Blocks   Id  System
/dev/[COLOR="Red"]sda1[/COLOR]   *           1       30820   247561618+   7  HPFS/NTFS
/dev/[COLOR="green"]sda2[/COLOR]           30821       34867    32507527+   5  Extended
/dev/[COLOR="blue"]sda5[/COLOR]           30821       31992     9414058+  83  Linux
/dev/[COLOR="blue"]sda6[/COLOR]           31993       34604    20980858+  83  Linux
/dev/[COLOR="blue"]sda7[/COLOR]           34605       34867     2112516   82  Linux swap / Solaris


[COLOR="Red"]sda1[/COLOR] is a primary partition
[COLOR="Green"]sda2[/COLOR] is an extended partition
[COLOR="Blue"]sda5 sda6 sda7[/COLOR] are logical partitions

you still have primary partition numbers sda3 & sda4

I'm not sure if an extended partition must be the last in the chain...
Since I've always made the first three as primary, used or not.
Then the extended as number 4, used or not.
this has always given me the most flexible scheme, with partitions in disk order.

---

### Post by DigiTan on 2009-03-22
Okay, so just to clarify: even if I just remake sda2 as a bigger partition, I'm going to loose data?  Even if I'm just expanding it onto empty disk space?  (Right now, the last 30GB of this disk is unpartitioned)

Will my sda1 partition be affected as well?

---

### Post by gali98 on 2009-03-22
I am going to guess that just resizing it will not cause data loss, but since it is a logical (with other partitions inside as far as I am understanding) I can't say for sure.
My best recommendation is to use gparted to do this.
sudo apt-get install gparted

It works quite well and informs you of what it is doing. (i.e. if data loss will occur.)
Kory

---

### Post by egalvan on 2009-03-23
> **DigiTan said:**
> just to clarify:
even if I just remake sda2 as a bigger partition, **I'm going to loose data**?  Even if I'm just expanding it onto empty disk space?  (Right now, the last 30GB of this disk is unpartitioned)

Will my sda1 partition be affected as well?

You will probalbly not loose data, but since this IS a computer,
wrtiting to a magnetic media, it IS POSSIBLE...
so if your data is important, MAKE BACK-UPS!

That said, to expand sda2, you need to boot with another system,,,
such as a LiveCD... partedmagicLiveCD, Ubuntu LiveCD...

run gparted and select the partition sda2... 
then right-click and select "resize/move" option...

either drag the right side of the partition, or change the numbers indicating the size...

once you are satisfied that your work looks good, then click "apply"

note that this only expands the EXTENDED partition, not any of the LOGICAL partitions inside of it...
these need to be resized/moved after the extended is resized.
(it's a two-step operation...
first make the container bigger, 
second makes the inside bigger...)

And sda1 would not be touched, unless you make changes to it.

---

### Post by DigiTan on 2009-03-23
Well, I halfway-tried this partition mission.  First thing: GParted would not give me a "resize" option for the extended partition itself, leaving me with cfdisk and fdisk.  

Second: CFdisk freaked me out because the extended partition itself was invisible and I'm not in the greatest position to experiment.  

Deleting sda2 in fdisk knocks out sda5, 6, and 7 along with it; and since Grub is my only route to Windows, I basically loose sda1 until my Win CD can restore the master boot record.  I rarely turn down an adverture, but I figure why do it now when I'll just repartition again next month?

Long story short: It's not over, but for now, I'm settling for this setup below.  I'll bump whenever I've picked this 2nd Linux...

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30820   247561618+   7  HPFS/NTFS
/dev/sda2           30821       34867    32507527+   5  Extended
/dev/sda3           34868       38781    31439205   83  Linux
/dev/sda4           38782       38913     1060290    b  W95 FAT32
/dev/sda5           30821       31992     9414058+  83  Linux
/dev/sda6           31993       34604    20980858+  83  Linux
/dev/sda7           34605       34867     2112516   82  Linux swap / Solaris
```

---

