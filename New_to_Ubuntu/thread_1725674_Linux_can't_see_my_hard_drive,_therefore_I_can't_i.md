---
title: "Linux can't see my hard drive, therefore I can't install it."
date: 2011-04-10
forum: New to Ubuntu
---

### Post by AndyM2612 on 2011-04-10
I've been using Windows Media Center for about 5 years now and would like to give Linux and MythTV a go.
 So I did a bit of research and downloaded Mythbuntu 10.10 and partitioned my hard drive accordingly(little confused about the SWAP partition though, is it necessary with 2GB RAM?), I then burnt the image to CD and attempted an install.
 I got up to the stage where you select which hdd/partition to install the OS onto at which point I did not get my chosen hard drive as an option.
 My system specs are a Gigabyte motherboard (socket1156) with the usual complement of hard drive connectors 1xIDE and 6xSATA
On these hard drives I have: 
hdd0/320GB IDE (320GB_NTFS_1xPrimaryPartition) containing DVR-MS Recorded TV files
hdd1/250GB SATA with multiple partitions:
(5GB_FAT32) acronis OS selector & windowspagefile (primary partition)
(20GB_NTFS) windows MCE 2005 (primary partition)(active)
(20GB_ext3) (primary partition) intended for linux, now realising that it may need an extra partition for swap, although my system has 2GB RAM? yet to researched?
(205GB_Extended Partition): 120GB_Logical_Drive_FAT32 (Audio & Video files)
                                          85GB__Logical_Drive_ex-fat (Temp Drive for burning etc..)
hdd2/1TB SATA (1TB_NTFS_1xprimarypartition) containing DVR-MS Recorded TV files
hhd3/2TB SATA (2TB_NTFS_1xprimarypartition) containing DVR-MS Recorded TV files 

 The only drive that is not visible is the 250GB on which I'd like to install Mythbuntu. I have not exceeded the 4 primary partition limit and I am baffled as to what I haven't done to prepare the drive for installation, although I have read that Linux may get confused with such a complex setup.
 Now I realise that the Windows partition is the active partition. Is it a matter of changing this temporarily (ie. make the Linux partition active) to allow Linux to install then once installed make the Acronis partition the active partition.
 The Acronis partition is not active but the programme is installed to the MBR and I would prefer to keep it as the default OS loader, understanding that Acronis would then boot the GRUB loader, which would be installed on the partition that Linux is to be installed on, which in turn boots Linux.
 Also I believe that I can customise the GRUB loader to boot Linux almost automatically (1 sec delay).

---

### Post by earthpigg on 2011-04-10
really non-nerdy solution, but potentially quick/easy:

try unplugging all but the one hard drive, just for the install, and plug that one hard drive into a place that you know ubuntu is seeing.

mythbuntu isn't going to explode if you plug them back in immediately after the successful install.

by my reckoning, that will also make it impossible for grub to override acronis even if you mis-click during the mythbuntu install.

---

### Post by AndyM2612 on 2011-04-10
O.k, I'll give it a go, but I don't see how changing the 250GB drive from SATA port 1 to SATA port 2 will make any difference.

---

### Post by norm7446 on 2011-04-10
Hi Andy can you see the H/Drive in the BIOS.

---

### Post by AndyM2612 on 2011-04-10
The hard drive can be seen by the bios. It has windows mce 2005 on it and it boots into that OS no problems.

---

### Post by norm7446 on 2011-04-11
OK. Is the 250Gig the First H/Drive the BIOS is booting from. As you have listed below that your 320gig Drive is Hdd1 which is disc two ?. 

Personally I would have used the 85Gig Drive and split it 40/60, and let grub boot to Myth or the Acroins manager, or even VM Windows MCE in Myth.

---

### Post by AndyM2612 on 2011-04-12
The 250GB is considered by the BIOS as the 2nd hard drive but it is the physically the first SATA hard drive. The arrangement goes as this: IDE Port=DVD/RW ROM~Master, 320GB~Slave : SATA 1=250GB~Master Drive,SATA 2=1TB~Slave Drive : SATA 3=2TB~Master Drive and my other 3 SATA ports SATA 4,5 & 6 Slave,Master & Master respectively, are free. I plan on adding 2 more data drives and a Blu-Ray to system to complete it. I had originally planned on using Apple OS 10.6.6 on the Linux partition and had arranged it in the same way I had read of, that worked for the Mac OS, in a Hackintosh forum. But I have since acquired In Android device and thought the spare partiton would be a good opportunity too finally take the Linux plunge, knowing that Android is just a variation of a Linux system and that my phone should integrate with it quite well. I am certainly no newb to computing and believe I have done all the necessary preparations required according to the 4 primary partition rule. Unless Linux is confused by my ex-fat(FAT64) partition, being so new, and choses not to mess with what it doesn't understand, as I've heard Linux can do. But being the latest version of the OS I would have thought it would at least treat it as an un-defragmentable FAT drive as all my defrag programmes in XP do.

---

### Post by Justbill on 2011-04-12
I don't know if this will help, you may want to take a look at this thread [http://ubuntuforums.org/showthread.php?t=1725847&highlight=Real+problem]("http://ubuntuforums.org/showthread.php?t=1725847&highlight=Real+problem") , I had a similar problem (I think) only difference was I have a single hard drive. I also was using "Media Center" on that machine, and somehow the 2nd partition and 3rd partition were overlapping. Using sfdisk I deleted the partitions that were not being used (careful here!) (there is a link to a good tutorial in the thread), creating free space, and then the partitioning tools were able to "see" my hard drive.
Not sure if this is the same problem you are having or not, hope it helps.

Bill

---

### Post by Justbill on 2011-04-12
I ended up using "Parted Magic", here is a link [http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start) . I REALLY liked this much better! Haven't used everything in it yet, but it contains a lot of good stuff (gparted, clonezilla, etc.)! Good luck too you!

---

### Post by Justbill on 2011-04-12
I don't know if you looked at this link yet, but it REALLY helped me! [http://ubuntuforums.org/archive/index.php/t-1192598.html](http://ubuntuforums.org/archive/index.php/t-1192598.html)

Bill

---

