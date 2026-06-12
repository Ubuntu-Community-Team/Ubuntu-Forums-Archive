---
title: "can't install ubuntu with win7 - partition editor not recognizing my pre installed wi"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by powel212 on 2009-11-15
Trying to install Ubuntu beside win7 but when I run the live cd and open the partitioner it says my drive is unpartitioned space, but windows is already installed and working.

There is only one drive in the box and it is plugged into SATA-0

Windows is a fresh install and there is tons of extra space on the drive.

I tried creating an extra partition from inside windows, No problem then restarted the live cd but partitioner still doesn't recognize the ntfs partitioned space or the secondary partition either.

What's up?

Powel

---

### Post by yanceypd on 2009-11-15
A couple of things to check.  Can you still bootup in windows?  Have you defraged the fresh install of windows?  Windows sort of tosses data around disk.  Have run test disk of installation CD?  When you get to the partioning section of installation the Windows OS should be there.  If it is there should be a slider on right side of displayed info that you can move to set partion size for Ubuntu.

---

### Post by Mark Phelps on 2009-11-15
First off, do NOT, repeat, do NOT use the Ubuntu installer to shrink the MS Windows OS partition.  Doing so runs the risk of corrupting the OS and rendering it unbootable.

Advise going to distrowatch.com, finding the GParted LiveCD, downloading it, and buring the image to a CD.

Then, boot with that and see if IT sees the partitions.

OH, and the second partition you created, did you format it as NTFS? IF so, THAT is the problem.  Ubuntu can't install in NTFS partitions.

If the GParted LiveCD sees all the partitions, then remove the extra partition you created and replace it with a partition formatted as Ext4 -- for Ubuntu.

Then, when you boot into Ubuntu LiveCD to do the install, choose Manual Partitioning and select the partition you just created.

---

### Post by powel212 on 2009-11-15
> A couple of things to check. Can you still bootup in windows? Have you defraged the fresh install of windows? Windows sort of tosses data around disk. Have run test disk of installation CD? When you get to the partioning section of installation the Windows OS should be there. If it is there should be a slider on right side of displayed info that you can move to set partion size for Ubuntu.

There are already 2 partitions on the drive. one is formatted as fat. Neither are recognized. The whole thing shows up in Gparted as unformatted space but it is actually a windows partition and yes windows boots and runs fine.

Powel

---

### Post by powel212 on 2009-11-15
> Advise going to distrowatch.com, finding the GParted LiveCD, downloading it, and buring the image to a CD.

Good idea i'll give it a shot. 

> OH, and the second partition you created, did you format it as NTFS? IF so, THAT is the problem. Ubuntu can't install in NTFS partitions.

It isn't recognizing the NTFS partition or the FAT partition. think this is not the issue.

I have installed ubuntu in Vbox and will run it that way for now. To be honest I'm not crazy about Koala. Liked Jaunty better. Look forward to the next release, though.

Powel

---

### Post by theozzlives on 2009-11-15
Use Disk Management that came with 7 to resize your drive!

---

### Post by sandyd on 2009-11-15
> **powel212 said:**
> There are already 2 partitions on the drive. one is formatted as fat. Neither are recognized. The whole thing shows up in Gparted as unformatted space but it is actually a windows partition and yes windows boots and runs fine.

Powel
use the windows partition manager to create free space
then at the ubuntu partitioning step, use "use largest continueous block of free space"

---

### Post by powel212 on 2009-11-15
> use the windows partition manager to create free space
then at the ubuntu partitioning step, use "use largest continueous block of free space"

Tried that too. Still shows as unformatted drive in ubuntu.

Powel

---

### Post by bwzz on 2009-11-15
Done the installation of KK from Win7 on NTFS disk and it worked fine. Even created a partition for Ubuntu from the installer itself.
Try running the setup inside Win7, instead of booting from the CD.

---

### Post by RJ12 on 2009-11-15
> **bwzz said:**
> done the installation of kk from win7 on ntfs disk and it worked fine. Even created a partition for ubuntu from the installer itself.
Try running the setup inside win7, instead of booting from the cd.

aka "wubi"

---

### Post by powel212 on 2009-12-09
As it turns out the problems were all caused because I had previously had the drive in one of my Mac machines. It had been formatted as 64Bit-GUiD. I stuck the drive back in a mac and formatted it to MBR and then Ubuntu and Windows recognized it correctly. One point of note is that only the Mac could get the drive back to its original state. Windows could format it but couldn't format it in Ubuntu friendly 32Bit MBR. 

Thanks for all the feedback.

Powel

---

### Post by kakashi_12 on 2009-12-09
cool you finally figured it out. the other thing to note is (maybe you know this already)... you should be able to JUST create the partition with the windows disc and NOT format it as any format, just a clean slate partition. then put the linux disc in and format it in ext4.

---

