---
title: "Ubuntu on external HDD?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-01-10
Hi, I have a few questions about what options I have at creating a truely portable Ubuntu.

I am currently rubbing a persistent live USB of Ubuntu as I make this post. It works fine, but with two issues. The disk space is limiting, and the live user has full root privileges without a sudo password. I know I can make a new user, but I don't like the idea of a user called "ubuntu" with no password and full root privileges hanging around. 

So. Here is my idea. I have an 80 GB external hard disk. Would I be able to install an actual copy of Ubuntu onto this HDD?

I am not willing to give up ALL the storage on that HDD for Ubuntu. What if I made three partitions, one for the Ubuntu OS, one for SWAP, and the third for data storage with FAT32 file system? I can boot Linux at any computer by interrupting startup and booting from USB. Is this realistic?

How would the booting work? Do I need to do any config (ie. specify the first partition for boot).

How about speed? Would running an OS from an external HDD be extremely slow? Also, would this shorten the life of my HDD (i heard it does for a USB, but an external HDD isnt a flash media)...

Sorry for the long post. If you've read up to here, thanks for your patience. I am looking forward to any tips.

---

### Post by jfr1tz on 2009-01-10
Yes you can install to an external HDD, booting from it depends on your bios support. 

You can make 3 partitions and install a bootloader on the external disk. Then press the key during startup to select a bootdevice and boot the external disk. You have to tell ubuntu during install to put the bootloader on the external disk however or it will put it on your internal hard drive.

speed depends, usb/firewire maxes out at 20Mb/s, eSata will be faster.

---

### Post by underdog512 on 2009-01-10
you can install a full version on ubuntu on the external hard drive but it would only work on the one computer because build Hardware Abstraction Layer (HAL) that is unique to that computer. So, if you try to boot it on a different PC its not going to work right. Thus making it not very portable.

---

### Post by akimatsu123 on 2009-01-10
> **underdog512 said:**
> you can install a full version on ubuntu on the external hard drive but it would only work on the one computer because build Hardware Abstraction Layer (HAL) that is unique to that computer. So, if you try to boot it on a different PC its not going to work right. Thus making it not very portable.

Could you explain that a little more? So HAL (whatever that is) is unique to every computer?

Well, just not having to repartition my entire hard disk and messing with my actual system is good enough as it is. Worst comes to worst, I can just 
format my HDD and everything is okay :D

---

### Post by akimatsu123 on 2009-01-10
Update:

Installation was entirely successful, with very little problems. Here is the procedure I followed should anyone else want to attempt this. I will try to keep this as GUI oriented as possible. 

I will assume that you still want to keep a partition for NTFS data storage.
Boot off a LiveCD or LiveUSB

[LIST=1]
[*]Unmount the HDD that you want to install Ubuntu on. 
[*]Go to System > Administration > Partition Editor
[*]Select the HDD that you want. BE SURE TO SELECT THE CORRECT HDD.
[*]Delete ALL PARTITIONS, and apply changes. Do not create any new partitions yet. 
[*]Exit GParted, and start install.
[*]Do the usual config until you get to the part with the partition manager
[*]Choose manual
[*]Now all of ur HDD, both internal and external should show up (they need to be unmounted!)
[*]We will create three partitions. One for Ubuntu's system files, one for SWAP space, and the remaining for storage. Make sure you pick the correct data types ("Ext32" for Ubuntu, "FAT32" for storage, "swap" for swap)
[*]The Ext32 partition should be the "primary" partition. Set its mount point to "/"
[*]Set the mount point of the FAT32 partition to "/dos"
[*]Check format where you can
[*]Press NEXT, and follow the instructions
[*]When you come to the last page (step 7 of 7) click advanced, and make sure "Install Bootloader" is checked, and that it will be installed to your external HDD. (not to any partition, just for example to "/dev/sdc")
[*]Let it install, boot from usb, grub comes up, pick ubuntu, and you have it :D

[/LIST]

---

