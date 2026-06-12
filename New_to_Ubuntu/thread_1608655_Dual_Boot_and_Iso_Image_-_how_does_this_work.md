---
title: "Dual Boot and Iso Image - how does this work?"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by sbmuser on 2010-10-29
Hello, 

I am new to this forum.

I am running Windows 7 64-bit already, and I know it's possible to install a dual boot with Ubuntu.
But sadly, that's all I know. I am a stickler about keeping my computer clean and not messed up. I am not familiar with a lot of **advanced **advanced computer terminology and procedure [if you get what I mean :) ].

The first question I have with installation is **what is an iso, or an iso image?** This was very confusing to understand from the forums, so can someone give me an exact definition please?

Second,** how does one "burn an iso image onto a CD"? **I understand what CD burning is, but the concept of iso image burning is a completely alien concept to me. 

Third, **how do you partition your hard drive**? I understand what it is, I just don't know how to do it. Is it essential that you need third party software? This was the most troubling concept for me, because I have heard that Ubuntu shrinks your Windows 7 hard drive space, and I don't want that to happen! Is there any way for me to partition my hard drive without losing space? I think I have enough to set aside for Ubuntu **on one hard drive**.

Fourth, just for future reference, **how do you use virtualbox with Ubuntu?** I have seen a LOT of posts on this, but I have no idea what virtualbox is beyond that it is a virtualization program, and how to use virtualbox with Ubuntu.

Fifth, **can Ubuntu also access my Windows applications (all that are compatible)** ?

Any help on these issues is greatly appreciated. Thank you!

---

### Post by tajiknomi on 2010-10-29
[SIZE=2][I]Welcome to Ubuntu forums:P
you can check .iso formate straight from Google..

2)You can use many open source soft like **K3b/Brasero** to burn cd with..

3)Use **Gparted** for partion...you can check it out from live-cd, i-e sys>Admin>Partition manager

4)Virtual Box ? follow the link [/I][/SIZE][http://www.youtube.com/watch?v=HL7kIqGXFrM&feature=related](http://www.youtube.com/watch?v=HL7kIqGXFrM&feature=related)

5)[SIZE=2]Yes sometime for some application using Wine[/SIZE], [SIZE=2]know about wine,..?follow this[/SIZE] ...[http://www.linux.com/archive/feed/54920](http://www.linux.com/archive/feed/54920)

---

### Post by Verbeck on 2010-10-29
> **sbmuser said:**
> 
The first question I have with installation is **what is an iso, or an iso image?** This was very confusing to understand from the forums, so can someone give me an exact definition please?

it is an image (exact duplicate) of a cd or dvd. ubuntu and almost all the linux distros are downloaded as .iso file
> 
Second,** how does one "burn an iso image onto a CD"? **I understand what CD burning is, but the concept of iso image burning is a completely alien concept to me. 
iso burning is burning the contents of the .iso file to a cd or dvd. in ubuntu, there is a native iso image burner, applications>Sound and video>brasiro. select the burn image option.
in windows, you can use imgburn and select the 'write image file to disk' option.
[http://www.imgburn.com/](http://www.imgburn.com/)
> 
Third, **how do you partition your hard drive**? I understand what it is, I just don't know how to do it. Is it essential that you need third party software? This was the most troubling concept for me, because I have heard that Ubuntu shrinks your Windows 7 hard drive space, and I don't want that to happen! Is there any way for me to partition my hard drive without losing space? I think I have enough to set aside for Ubuntu **on one hard drive**.
ubuntu shrinks your harddrive if you try to install them side-by side in the installer. use manual method if you want to install in on a separate partition
+free up disk space in windows then 
+use gparted in the ubuntu live cd to shrink the windows partition use gparted in the live cd to shrink the partition(system>administration>gparted). 
+and then while installing, try manual install. create a new ext4 partition with the mount point as / (or separate / and /home drives)

more info
[https://help.ubuntu.com/community/Partitioning](https://help.ubuntu.com/community/Partitioning) 
> 
Fourth, just for future reference, **how do you use virtualbox with Ubuntu?** I have seen a LOT of posts on this, but I have no idea what virtualbox is beyond that it is a virtualization program, and how to use virtualbox with Ubuntu.
you can download it from [http://www.virtualbox.org](http://www.virtualbox.org)
the gui is easy to understand, so once installed, just follow the on-screen instructions

> 
Fifth, **can Ubuntu also access my Windows applications (all that are compatible)** ?
even if you have wine installed, only a very few times you can run it off from the windows partition. even if its listed as compatible at wine appdb.

---

### Post by Matt__ on 2010-10-29
to start with I suggest you [_download ubuntu iso_](http://www.ubuntu.com/desktop/get-ubuntu/download) to your windows desktop.

As you dont already have an ubuntu disc, use a 3rd party windows burning software to burn this .iso file to a disk. many many burner programs can create a disc from an .iso...or you can use this free [_cd burner xp_](http://cdburnerxp.se/en/home) (I have used it in win7 a few times..very simple to use, install/open/select burn iso/choose file...done).

now you can try ubuntu straight form the disc...put it in your cd drive..reboot..select boot from cd (via the bios or F9/F12)..select 'try ubuntu'.

this way you can see if you like ubuntu, check if it needs aditional drivers, and that wireless works (if required).


Later if you decide to install Ubuntu you can either select an already created partition from windows or any other hard drive you have (ubuntu really needs to be on the primary master drive to avoid bootloader probs), or use a slider/specific value to select how much space you want to give the new OS during the install process.


Ubuntu can run certain windows programs, but not natively, you would have to install WINE, but you can access you window files from ubuntu just by navigating to them as you would in windows. There are many native programs that do pretty much anything windows can and thousands more in the repositories.

As to virtual box, yes..it allows you to run other operating systems within the main one you are using. You can in theory run ubuntu virtually this way from within windows (you can also install ubuntu via WUBI, that is..as a folder that runs the whole operating system within windows(performance may suffer))

Equally you could use virtualbox or similar to run other linux distros in ubuntu, or even virtual windows OS. again..these will not run as well as operating systems that are actually installed.

---

### Post by sbmuser on 2010-10-29
Thanks a lot for the help! I feel a lot more confident in installing Ubuntu now. I am actually burning the iso now (yay! I understand this! )

Cheers

---

### Post by oldfred on 2010-10-29
If you are shrinking your windows partition, be sure to use the windows tools in the window MMC. Then reboot windows several times as it will want to confirm its new size and probably run chkdsk. Then you can install Ubuntu.

Some examples so you can see what will happen:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

Also some examles of using gparted.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Recognize that Ubuntu is not windows, but another operating system. Some applications are almost identical like Firefox or Thunderbird, but have been written to work the same. Some applications will not run in Ubuntu, and do not run or not run well in wine.
Linux alternatives to windows apps
[https://help.ubuntu.com/community/ListOfOpenSourcePrograms](https://help.ubuntu.com/community/ListOfOpenSourcePrograms)
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

---

