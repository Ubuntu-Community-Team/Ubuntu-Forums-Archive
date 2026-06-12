---
title: "Rename internal drive"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Gemu on 2008-12-10
Greetings, I am new to linux, Ubuntu and the command line to do anything. I really like it a lot the more I use it. I was wondering if there is an easy way to edit the internal master drive to something like /dev/sda/1,2,3,4,5,6 as opposed to /dev/sda2,5,6,7,8?? 


 Its not that big a deal they're a tad harder to keep track of when they skip around like that. Thanks in advance.

---

### Post by Hospadar on 2008-12-10
What exactly are you asking?
Linux will automatically assign each drive to some /dev/sda# and there isn't a whole lot you can do about that.
What you can do is change the mount point (generally your non-root drives are mounted in /media/something).  The way linux keeps track of which drive is which is with something called a UUID, it's a unique identifier for each partition.

If you open up your /etc/fstab file (which controls drive mounting) you'll see the UUIDs of all your drives, and their corresponding mount points.  Here's my file:
```
  GNU nano 2.0.7                      File: /etc/fstab                                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ad070f84-db98-4d31-8788-37e35b902c40 [COLOR=Red]**/**[/COLOR]               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=107f6517-b494-4af1-b033-5e8150d3ad71 [COLOR=Red]**/home**[/COLOR]           ext3    relatime        0       2
# /dev/sda1
UUID=AEE09EF6E09EC3CD [COLOR=Red]**/media/windows**[/COLOR]  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=c18b47fc-f05b-4f54-9f9c-70ce57623ee7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```I bolded the mount points, If you want to change the name of the folder where the drive is mounted to, just edit its mount point in the fstab file.

Important!  
-Make sure to backup your /etc/fstab file before you touch it, maybe keep a livecd on hand.  If you're just changing mount points, probably not a big worry, but better to be safe.
-Don't change the mount points of the partitions mounted to "/" or "/home" these are your root and home partitions (Don't worry if you don't have a /home, that's a special thing you can do in installation)
-You may want to create an empty folder in /media before you set a mount point to something.  For example, you want some drive to mount to /media/mydrive, first "sudo mkdir /media/mydrive".  I'm not sure this is necesary, but I always do it.

To edit your /etc/fstab, Alt-F2 (or terminal) and type "gksu gedit /etc/fstab"

---

### Post by rhcm123 on 2008-12-11
> **Gemu said:**
> Greetings, I am new to linux, Ubuntu and the command line to do anything. I really like it a lot the more I use it. I was wondering if there is an easy way to edit the internal master drive to something like /dev/sda/1,2,3,4,5,6 as opposed to /dev/sda2,5,6,7,8?? 


 Its not that big a deal they're a tad harder to keep track of when they skip around like that. Thanks in advance.

are you talking about labeling them? might i then suggest tune2fs?
```
 tune2fs -L THEDRIVE /dev/sda1  
```

this names the drive at /dev/sda1: THEDRIVE

---

### Post by Gemu on 2008-12-11
Here is a copy of my fdisk -lu results-


 Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   390716864   195358401    5  Extended
/dev/sda5        19535103   382909274   181687086   83  Linux
/dev/sda6       382909338   390716864     3903763+  82  Linux swap / Solaris
/dev/sda7             189      192779       96295+  83  Linux
/dev/sda8          192843    19535039     9671098+  83  Linux



 I was just wanting my drives to be sda1, sda2 sda3, etc. its not that big a deal until you mess with grub a bit. Every time you reload the system you get a new master drive name. 


 I reinstalled my system so I could get a separate boot partition and left my separate home partition like it was and now if you open up gparted the first drive in there is -

sda2 extended   
sda7 thats my boot partition
sda8 is my / partition
sda5 is my home partition
sda6 is my swap partition

 root was sda1 and home was sda3 and swap was sda5. I could deal with that but now my first partition is sda7 and my 2nd is sda8. The sda2 extended seems to name the entire drive with the others as subdirectorys. It just seems a tad odd to me. Thanks for the replys.

 Crazy, crazy :lolflag:

---

### Post by rhcm123 on 2008-12-11
> **Gemu said:**
> Here is a copy of my fdisk -lu results-


 Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          63   390716864   195358401    5  Extended
/dev/sda5        19535103   382909274   181687086   83  Linux
/dev/sda6       382909338   390716864     3903763+  82  Linux swap / Solaris
/dev/sda7             189      192779       96295+  83  Linux
/dev/sda8          192843    19535039     9671098+  83  Linux



 I was just wanting my drives to be sda1, sda2 sda3, etc. its not that big a deal until you mess with grub a bit. Every time you reload the system you get a new master drive name. 


 I reinstalled my system so I could get a separate boot partition and left my separate home partition like it was and now if you open up gparted the first drive in there is -

sda2 extended   
sda7 thats my boot partition
sda8 is my / partition
sda5 is my home partition
sda6 is my swap partition

 root was sda1 and home was sda3 and swap was sda5. I could deal with that but now my first partition is sda7 and my 2nd is sda8. The sda2 extended seems to name the entire drive with the others as subdirectorys. It just seems a tad odd to me. Thanks for the replys.

 Crazy, crazy :lolflag:


It was probably because when you installed the partitoner saw that the patiton numbers sda1,3, and 5 were in use, so it just randomly selected others and used them. :)

---

### Post by Gemu on 2008-12-14
Yeah I guess so. I was setting up grub to boot several os's and It just blows me away that my 2nd partition is listed as dev/sda 8 and grub sees it as hd0,7 . I guess if I have to live with it I will. Thanks.

---

### Post by Gemu on 2008-12-17
I think I found the answer to my question. Instead of renaming hard drives apparently if you set up partitions right to start with with fdisk or cfdisk then they follow a /dev/sda1,/dev/sda2, /dev/sda3 order. Gparted seems to skip around a bit.


 Here is a nice link on partitioning with fdisk. [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html#mixed]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html#mixed") 



 I'm soon going to re-install my system, partitionioning with fdisk or cfdisk.

---

### Post by vanadium on 2008-12-17
You are worrying about a non-issue. Your system can work perfectly as currently partitioned, although indeed it is not usual to have only logical partitions.

---

### Post by rhcm123 on 2008-12-19
> **vanadium said:**
> You are worrying about a non-issue. Your system can work perfectly as currently partitioned, although indeed it is not usual to have only logical partitions.

Wait, the partitions are only logical? Hm.... that is odd.. i didn't know the computer would run that way. :)

---

### Post by vanadium on 2008-12-20
> Wait, the partitions are only logical?
That is what is apparent from the output of fdisk -l. Linux can be installed anywhere. MS Windows (at least older versions) needs to be on a primary partition (I believe).

---

### Post by shalomhk on 2008-12-20
If you download and burn to disk GParted, restart your computer and boot from the new CD......... you can change your disk partitioning as well as labels, mount points and flags.

---

### Post by Gemu on 2009-01-02
Hey you guys, I got it fixed. Look at my fstab now.




guest1@guest1-desktop:~$ sudo fdisk -lu
[sudo] password for guest1: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     9783584     4891761   83  Linux
/dev/sda2         9783585    29334689     9775552+  83  Linux
/dev/sda3   *    29334690    29543534      104422+  83  Linux
/dev/sda4        29543535   390716864   180586665    5  Extended
/dev/sda5        29543598    37367189     3911796   82  Linux swap / Solaris
/dev/sda6        37367253   390716864   176674806   83  Linux

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047e91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    30716279    15358108+   7  HPFS/NTFS
/dev/sdb2        30716280    50251319     9767520   83  Linux
/dev/sdb3        50251320   126415484    38082082+   5  Extended
/dev/sdb4       126415485   171477809    22531162+   b  W95 FAT32
/dev/sdb5        50251383   108840374    29294496   83  Linux
/dev/sdb6       108840438   118607894     4883728+  83  Linux
/dev/sdb7       118607958   126415484     3903763+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000aec92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   103538924    51769431    b  W95 FAT32
/dev/sdc2   *   103538925   123073964     9767520    b  W95 FAT32
guest1@guest1-desktop:~$ 




  1,2,3,4,5,6,7   Thats what I'm talking about.:P  I used cfdisk to partitition before I installed everything instead of gparted. 


I have Knoppix on HD1 1st partition and Ubuntu on the 2nd.

XP Proff is first on the 2nd HD 1st partition and a backup Ubuntu system is one its 2nd Partition.

---

