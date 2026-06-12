---
title: "Unallocated Partition"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by coffeemadman on 2009-07-23
I am completely new to this, so please go easy on me!

When I look at my disk management on Vista, I see Vista on the C drive, taking up 93GB or so. Then I have another 93GB of unallocated space. 

Firstly. I'm not sure what that is, or why my computer is only utilising a half of its hard drive.

Secondly. When I try to install Ubuntu, it says I have no operating systems on my computer and that there is around 180GB of free space.

I don't want to lose Vista, but Ubuntu seems to be saying it will wipe my whole computer if installed.

How do I install it on the unallocated space? (Is it possible?)

---

### Post by jerome1232 on 2009-07-23
From the Ubuntu live cd, upload a screenshot of gparted (System - Administration - Partition Editor) or paste the results of running this command from a terminal (Applications - Accessories - Terminal)

This way we know what ubuntu is seeing.
```
sudo fdisk -l
```

---

### Post by louieb on 2009-07-23
You should be able to use the unallocated space. Depending on your partition layout.  

Do you have Internet with the live CD If so open System>Administration>Partition Editor. Use alt+prt screen to take screen shot of the Gparted window. Please attach to your next post.

Oh -  a day late and a dollar short agin.

---

### Post by coffeemadman on 2009-07-23
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64d63c35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       12352    97680416    7  HPFS/NTFS
/dev/sda3           12352       24322    96141312    6  FAT16
ubuntu@ubuntu:~$ 

```

This is what I get from Ubuntu.

---

### Post by lindsay7 on 2009-07-23
Is a really old computer?  You have a partition which is formatted fat16.  Do you use this for anything.  Do you have any idea how it got that way.  Also the unknown file system is less then 2 gigs.  Any idea how that partition got that way?  We just need to make sure that nothing strange is going on here.

---

### Post by louieb on 2009-07-24
> **coffeemadman said:**
> 
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, [COLOR=Red]24321[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64d63c35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192       12352    97680416    7  HPFS/NTFS
/dev/sda3           12352       [COLOR=Red]24322[/COLOR]    96141312    6  FAT16
ubuntu@ubuntu:~$ 

```This is what I get from Ubuntu.

Kind of surprised fdisk did not give you a waring about sda3 running past the end of disk. Anyway thats why the installer shows your disk as one big empty area of space 

Should be safe enough to delete sda3. 
Can you browse sda3 using the live CD? Does the Partition editor  show 3 partitions. 

 My guess is Gparted  shows an empty disk also. In that case cfdisk would be the next most user friendly way to select and delete the partition. 
```
sudo cfdisk
```

---

