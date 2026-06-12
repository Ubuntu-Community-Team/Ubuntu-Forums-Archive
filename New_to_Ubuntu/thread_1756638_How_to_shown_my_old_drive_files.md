---
title: "How to shown my old drive files"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by whiterose on 2011-05-12
Hi
I am Joshua from India, today I have installed ubuntu in one of my system. It's working fine. but before my system was installed by win XP & there were c,d,e,f,g (Hard disk has - 5 partitions)

I formatted & stored ubuntu on only c drive( I hope so)

My hard disk size 160GB
Disk utility shown 

42 GB ext4 in one group
partitions flag bootable
device /dev/sd1
mount point Mounted at /
type Ext4
partition type linux (0x83)

Another grop - Extented 118 GB ( It has 4 parts)
29 GB swap space
Unknown 29 GB
29 GB swap space
30 GB swap space

29 GB swap space shows the following
partition type HPFS/NTFS (0 x07)
Device /dev/sda5


I'm very new to Ubuntu having no knowledge.

I have 15 systems in my office I want to install ubuntu in all system 

Please tell me how I Install & backup all my files in other drives

All the 15 systems - Windows installed in C drive only.
All  our working files are there in other drives.

Advanced Thanks.

---

### Post by astex on 2011-05-12
Your windows partition is the last partition (/dev/sda5).  It can be mounted using:

```
$ mkdir ~/mp
$ sudo mount -t ntfs-3g /dev/sda5 ~/mp
```

This will make your Window's C Drive appear in your home directory as the folder 'mp'.

I would recommend backing up by copying the necessary files to an external drive.

Your hardware (RAM specifically) will determine how much swapspace you  will need.  On a modern computer, 1GB should suffice and you will  certainly not need more swap space than you have RAM.

Lastly, it is generally a good idea to create a '/home' partition when installing.  This is where all of your personal files will go.  For my personal setup, my '/' partition is only about 8GB, my home partition is about 150GB, and my swap partition is 1GB.

---

### Post by Hedgehog1 on 2011-05-12
> **whiterose said:**
> I am Joshua from India

Another grop - Extented 118 GB ( It has 4 parts)
[B]29 GB swap space
Unknown 29 GB
29 GB swap space
30 GB swap space[/B]


Joshua,

Based on the number of swap spaces you have on this drive, I am guessing you installed Ubuntu a number of times on this system as you were experimentation with Ubuntu. You only need one swap space, by the way.

Ideally we want to get you to a more controlled install, lets get a look at the partitions on this first system and create a game-plan to ease the pain of installing Ubuntu on your other systems, too.

Please do this on the one system you have already installed with Ubuntu-

Boot off the Ubuntu LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

