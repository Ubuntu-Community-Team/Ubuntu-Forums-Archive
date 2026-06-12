---
title: "Ubuntu 10.10 Netbook"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Edward in CT on 2010-11-28
I have an Acer Apire One Netbook with Windows 7 Starter in one partition and Ubuntu 10.04 in another.  I want to replace the 10.04 with 10.10 netbook.  I made a flash drive which boots up, but I can't figure out how to erase the 10.04 partition and install the 10.10 partition.  Is there any instructions on the web?  I am a total beginner.

Thanks

Ed

---

### Post by Foxheadz on 2010-11-28
just tell it to install 10.10 on the same partition as 10.04

---

### Post by fooman on 2010-11-28
boot from the usb flash drive,  start the install and when you get to the "allocate drive space" screen....choose "specify partitions manually"

at the next screen you can delete or change the partitions of your choice.  the windows partitions will be easy to spot as they are "ntfs" or "fat".  the ubuntu ones will likely be ext4.  
you can choose to just "change" the partition,  then at the next screen choose to format the partition....that will erase any data on the partition.
if you choose to "delete" the partition....that will leave you with unallocated space in which you will have to create a new partition before continuing.

---

### Post by zeroseven0183 on 2010-11-28
Once you get to the portion where it asks you how it is going to be installed, select Manual specify. Then look for the partition where 10.04 is installed. You'll see there a couple or more partitions -- NTFS (for your Windows 7), EXT4 for the Ubuntu 10.04 (assuming you installed it before using EXT4 file system), swap partition... and if you have other partitions.

You mark that same partition (where Ubuntu 10.04) is, and format it and click Forward.

Be sure you have all your important data backed up before you do anything to your system. It's good to be ready.

We're here to guide you.

---

### Post by Edward in CT on 2010-11-29
I got to the "Allocate drive space" screen where I click to specify the partitions manually, but the only thing listed in the partition table is " /dev/sda"  Below under boot loader it says "Device for boot loader installation"  and then lists /dev/sda ATA Hitachi HTSS4501 (160 GB).  It doesn't list any partitions, just the whole disk drive.  What do I do next?

---

### Post by onaridge on 2010-11-29
All I did was click upgrade and it knew where to go. I had 10.04 installed. I had partitions as follows: root, home and swap partitions with Windows 7 on the other partition. I was actually kind of surprised how easy it was altho' it took several hours. I did have an external drive attached an used a cd.

---

