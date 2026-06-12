---
title: "Big problem about partition"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by prabhata on 2010-07-26
Brothers and sisters,
Regards.
I have 160 GB of HDD. I have dual booting system. One is XP and other is Ubuntu 10.04 lucid.

:(I knowingly did partition for both operating system 80 GB each. But b/c of my lack of knowledge i did mistake.Following is situation of my HDD which i can see in system--administration--Disk utility....

1) One block is Now XP is showing 77 GB 

2) 2nd block is showing 2.7 GB. It is showing free and it is ready to create partition.

3) Third block is 2.7 GB and it is my file system ubuntu 10.04 lucid

4) Fourth block is showing 74 GB and is free and ready to create partion means it is empty.

5) Other two blocks are showing 1.5 GB each and that is swap space.

I want my Ubuntu on maximum part of my HDD b/c i work on Ubuntu. Pls tell me how can i do this ? How can i merge all free space in ubuntu 10.04 ? Without this i can't do any work b/c of very little space.

Pls help..

---

### Post by viralmeme on 2010-07-26
> **prabhata said:**
> How can i merge all free space in ubuntu 10.04 ? Without this i can't do any work b/c of very little space.

What does [Qparted]("http://gparted.sourceforge.net/screenshots.php") show?

[IMG]http://gparted.sourceforge.net/screens/gparted_1_small.png[/IMG]

---

### Post by tarps87 on 2010-07-26
> **prabhata said:**
> Brothers and sisters,
Regards.
I have 160 GB of HDD. I have dual booting system. One is XP and other is Ubuntu 10.04 lucid.

:(I knowingly did partition for both operating system 80 GB each. But b/c of my lack of knowledge i did mistake.Following is situation of my HDD which i can see in system--administration--Disk utility....

1) One block is Now XP is showing 77 GB 

2) 2nd block is showing 2.7 GB. It is showing free and it is ready to create partition.

3) Third block is 2.7 GB and it is my file system ubuntu 10.04 lucid

4) Fourth block is showing 74 GB and is free and ready to create partion means it is empty.

5) Other two blocks are showing 1.5 GB each and that is swap space.

I want my Ubuntu on maximum part of my HDD b/c i work on Ubuntu. Pls tell me how can i do this ? How can i merge all free space in ubuntu 10.04 ? Without this i can't do any work b/c of very little space.

Pls help..

The answer is yes. Boot using the live cd, open gparted and expand the Ubuntu partition so that it fills the free space.

Note: All partitions that will be effected must be unmounted

---

### Post by prabhata on 2010-07-26
> **tarps87 said:**
> The answer is yes. Boot using the live cd, open gparted and expand the Ubuntu partition so that it fills the free space.

Note: All partitions that will be effected must be unmounted


I did boot with live CD. And first i went in System---administration---disk utility. And same partitions are showing what i have written earlier. 

then i went in System--administratiion-- Gparted. And many partitions are not showing. It is showing only one. It is written "Unallocated 149.05 GIB" . So volumes are not showing in Gparted. When i clicked on the partition then message is coming-- "Invalid partition table on  /dev/sda--wrong signature 0".

Okay pls see....
It is very kind for you all to give your valuable time.
Thank you..

prabhata

---

### Post by prabhata on 2010-07-26
> **viralmeme said:**
> What does [Qparted]("http://gparted.sourceforge.net/screenshots.php") show?

[IMG]http://gparted.sourceforge.net/screens/gparted_1_small.png[/IMG]
No, brother in Gparted it is not looking like yours. Just one allocated partition is showing. Means whole harddisk is showing unallocated.

---

### Post by prabhata on 2010-07-27
pls help. Or pls someone tell me is this problem can't be solved ?

Will i be able to merge all other partitions for Ubuntu ?
Why partitions are showing in Disk utility and not showing in Gparted ?
Pls help....

---

### Post by adamjkok on 2010-07-27
> **prabhata said:**
> pls help. Or pls someone tell me is this problem can't be solved ?

Will i be able to merge all other partitions for Ubuntu ?
Why partitions are showing in Disk utility and not showing in Gparted ?
Pls help....
I'm not much of a GParted expert, but I would say, judging from my personal experience, it's probably not fixable. Get some opinions from other users who may be better in this area first, but I would say to back up important data (if possible) and do a low-level format from a livecd (GParted comes as a standalone Linux distro with mlterm and a few other basic utilities).

---

### Post by tarps87 on 2010-07-27
Can you post the output of
```
sudo fdisk -l
```

---

### Post by prabhata on 2010-07-27
> **tarps87 said:**
> Can you post the output of
```
sudo fdisk -l
```

I did it brother and i am pasting it below.
The sda1 is my XP. After that it is showing in disk utility 2.7 GiB empty unallocated. but here it is not showing. sda2 is showing in disk utility 80 GiB extended and below of that sda5 is swap and sda6 is my ubuntu 10.04. And one other part is showing in disk utility that is 74 GiB unallocated.

In disk utility in first half there are two blocks. One is  xp and other 2.7 GiB is unallocated. And other half is showing 80 GiB extended and the below part of this 3 blocks are made. First is linux and second is unallocated and third is swap.

baba@baba:~$ sudo fdisk -l
[sudo] password for baba: 
omitting empty partition (7)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b0b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9376    75309023+   7  HPFS/NTFS
/dev/sda2            9702       19457    78359905+   5  Extended
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris
/dev/sda6            9702       10155     2763335+  83  Linux

Partition table entries are not in disk order
baba@baba:~$

---

### Post by viralmeme on 2010-07-27
> **prabhata said:**
> 
/dev/sda2            9702       19457    78359905+   5  Extended
`/dev/sda2 .. Extended' seems to be the problem, sorry I can't help you, it's a total mess ...

---

### Post by tarps87 on 2010-07-27
Either I'm missing something or something strange is going on, can I have the output of this please
```
sudo parted -l
```

I am currently trying to recreate you set up so it may take a while

---

### Post by tarps87 on 2010-07-27
Just checking over everything it looks like a corrupt partition table.
Have a read of this, I have never had to use it so don't know how successful it would be.
[http://ubuntuforums.org/showthread.php?t=370121](http://ubuntuforums.org/showthread.php?t=370121)

---

### Post by prabhata on 2010-07-27
> **tarps87 said:**
> Either I'm missing something or something strange is going on, can I have the output of this please
```
sudo parted -l
```I am currently trying to recreate you set up so it may take a while

I  did it and following is the result---

baba@baba:~$ sudo parted -l
Error: Invalid partition table on /dev/sda -- wrong signature 0.          
Ignore/Cancel?

---

### Post by tarps87 on 2010-07-28
That confirms it then, it looks like you will need to repair the partition table, the previous link I posted should guide you through this, don't forget to back up all important data first.

---

