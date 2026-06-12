---
title: "BIG PROBLEM: I've got no partition left"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by ppb7 on 2009-10-06
I don't know if this is the right place to post this question, but it is a typicaly newbie-like major mistake, I suppose.
I had a PC with xp and jaunty on dual-boot.When I got home earlier today and turned my PC on, I must have done something wrong because now it won't boot, all I get is:
Searching for boot record from IDE-0..ok
GRUB loading stage1.5
GRUB loading, please wait
Error 22.

My guess is that I've lost the partitions and the indexing that goes with them, but  that the data is still there. So my question is: how can I get it back?
Any help or suggestions will be greatly appreciated



LATEST: checking the router setup interface, I found out that the ubuntu partition of the drive is recognised as being connected to the router

---

### Post by ptn107 on 2009-10-06
You need an Ubuntu 9.04 live CD to fix this.  Boot it to the live CD desktop (the 'Try Ubuntu without any change to your computer' option.)  Go to Applications -> Accessories -> Terminal and type:
```
fdisk -l
```
press enter and paste the output you get here so we can help.

---

### Post by ppb7 on 2009-10-06
> **ptn107 said:**
> 
```
fdisk -l
```
press enter and paste the output you get here so we can help.
Fantastic to get an answer so quickly, thank you! I am however hesitant as to whether I should do straightaway what you've just said because I would like to be assured that the windows xp partition is not going to be damaged. What does that command do?

---

### Post by CharlesA on 2009-10-06
It lists what partitions fdisk finds. It'll tell you if the partitions are still there or not. It doesn't modify anything.

My first thought on this is that hdd died, but try using fdisk -l to check.

---

### Post by oldos2er on 2009-10-06
fdisk -l lists your hard disks, and their partitions. It's purely informational, and doesn't change anything on your disks.

---

### Post by ppb7 on 2009-10-06
> **CharlesA said:**
> My first thought on this is that hdd died, but try using fdisk -l to check.
That's what I'm afraid of but as i do not, strictly speaking, "own" the computer and the owners  are windows people, i wish to make sure that in the worst case scenario I could still get back the data on the drive.

---

### Post by Cheezespread on 2009-10-06
If the drive isn't dead ( which we hope ) , you could recover your windows drive without much effort using your recovery cd of Windows ( which i again hope you have  ;) ) . Or you could use SUpergrub boot disk to get the windows drive booting again by changing the MBR ( Master Boot Record ).

---

### Post by ppb7 on 2009-10-06
> **ptn107 said:**
> You need an Ubuntu 9.04 live CD to fix this.  Boot it to the live CD desktop (the 'Try Ubuntu without any change to your computer' option.)  Go to Applications -> Accessories -> Terminal and type:
```
fdisk -l
```press enter and paste the output you get here so we can help.
here are the results of what you suggested:
> 
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ 
This, I assume, means that i have no partition, doesn't it, since nothing is listed

---

### Post by ptn107 on 2009-10-06
Prefix the command with 'sudo' and it will display correctly.
```
sudo fdisk -l
```

---

### Post by ppb7 on 2009-10-06
> **ptn107 said:**
> Prefix the command with 'sudo' and it will display correctly.
```
sudo fdisk -l
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb231b231

   Device Boot      Start         End      Blocks   Id  System

---

### Post by halitech on 2009-10-06
ummm that doesn't look good at all. you have no partitions on the drive at all. Was someone playing around in Windows and deleted something they weren't supposed to?

fdisk -l should result in something like this
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 seectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7bbb99b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648       19209   125001765   83  Linux
/dev/sda3           19210       19457     1992060   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051741

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         668     5365678+   7  HPFS/NTFS
/dev/sdb2             669       38913   307202962+  83  Linux

```

---

### Post by CharlesA on 2009-10-06
Ugh I cringed when I saw that. Looks like all the partitions are wiped.

---

### Post by oldos2er on 2009-10-06
That disk would appear to be bare. There is a data recovery program called Testdisk available, if you need it. See [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by CharlesA on 2009-10-06
> **oldos2er said:**
> That disk would appear to be bare. There is a data recovery program called Testdisk available, if you need it. See [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

Thanks for the link! That'll be a handy tool to add to my toolkit. :-)

---

### Post by ppb7 on 2009-10-06
> **CharlesA said:**
> Ugh I cringed when I saw that. Looks like all the partitions are wiped.
But are the data still recoverable?

---

### Post by CharlesA on 2009-10-06
> **ppb7 said:**
> But are the data still recoverable?

Not sure, but give TeskDisk a shot. See the link above.

---

### Post by halitech on 2009-10-06
possibly with the use of a program like testdisk. According to here you can run testdisk from the Ubuntu live cds

[http://packages.ubuntu.com/search?keywords=testdisk](http://packages.ubuntu.com/search?keywords=testdisk)

---

### Post by ppb7 on 2009-10-07
> **oldos2er said:**
> There is a data recovery program called Testdisk available, if you need it. See [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)
given that l apparently love making a mess of things, the prospect of recovery is fantastic. but when I got to the site, since i had an XP partition and a linux one, I couldn't decide which to choose. Should i create a FreeDos live CD or can I install the Testdisk package that comes with jaunty.
Also, this may be a naive question but, as I haven't got a linux computer and have to run things through a live cd, can I still install testdisk or create a freedos live cd :?:

---

### Post by ppb7 on 2009-10-07
> **oldos2er said:**
> See [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)
It worked and both partitions as well as the data have been!
Thanks a million million, oldos2er!
What I liked particularly about the site was the possibility to go through the process step-by-step ([_here_]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")) which is a boon for somebody like me who's likely to make the most stupid mistakes.
Thanks again! :P:)

---

