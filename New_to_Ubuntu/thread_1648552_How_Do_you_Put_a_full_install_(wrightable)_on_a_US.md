---
title: "How Do you Put a full install (wrightable) on a USB Drive?"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Mtrboat01 on 2010-12-18
Due to the fact that i am being forced to share a laptop computer i am not able to do a full install or partition the hard drive . i would love to have ubuntu back in my life. If there is anyone that can tell me how to install Ubuntu on a USB 2.0 4Gig drive. Please let me know.
I think you can install to a usb drive and make it just like it was in the computer . i can make the laptop boot from the usb device first. Thank You for your help .

---

### Post by lmarmisa on 2010-12-18
If you wish an Ubuntu  full installation without modify any Windows partition, consider to use a virtualization type solution. 

I re***mend VirtualBox. It works really great:

[http://www.virtualbox.org/](http://www.virtualbox.org/)
[URL="http://www.virtualbox.org/attachment/wiki/Screenshots/ubuntu-on-xp.png"]
http://www.virtualbox.org/attachment/wiki/Screenshots/ubuntu-on-xp.png[/URL]

[http://www.virtualbox.org/attachment/wiki/Screenshots/vbox_under_vista_in_vbox_under_xp.png](http://www.virtualbox.org/attachment/wiki/Screenshots/vbox_under_vista_in_vbox_under_xp.png)

Install VirtualBox as any other Windows program and then you will be able to create one or more Ubuntu installations running as virtual machines.

Best regards,

Luis

---

### Post by jmszr on 2010-12-19
Mtrboat01,

I think this is what you're looking for: [http://mis.lewisu.edu/blogs/mgodfrey/installing-persistentbootable-ubuntu-1004-os-usb-drive](http://mis.lewisu.edu/blogs/mgodfrey/installing-persistentbootable-ubuntu-1004-os-usb-drive).

Hope that helps.

---

### Post by JustinR on 2010-12-19
Using the Startup Disk Creator like suggested above doesn't give the "full install" necessary, if you have to install drivers for your ***puter it will fail with that.

If you want a full install, just insert an Ubuntu live cd with the flash drive plugged in, and select the flash drive as the installation destination, instead of selecting a hard drive.

---

### Post by C.S.Cameron on 2010-12-19
It would be better to have more than 4GB for a flash drive but here is how I did a 4GB flash drive Full install step by step for 10.10.


Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 400MB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 2.77GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 600MB, Beginning, Ext2, and Mount point = "/home" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by beew on 2010-12-19
Hi,

I think you should have at least 8G to consider a full installation. 4G is doable, but it would be very tight.

Also, in addition to C.S. Cameron's excellent step by step tutorial I would suggest that you add a swap partition for about 512M. The windows partition and the /home partition wouldn't be necessary on the other hand IMHO because you are installing on a usb, it is not likely you would store a lot of stuffs there. You only need the windows partition if you need windows to be able access your portable Linux system. I can't really see any reason for that. Your Linux system would be able to access the Windows files in the hard drive when you boot from the usb so if you download something through Ubuntu you would be able to store it in your hard drive anyway.

A problem with full installation in an usb would be speed. It tends to be slow, and a lot slower than a live usb with persistence (which runs in ram) An ideal way to make a portable system would be to install in an external hdd instead. But if you prefer to install in a usb, you can make it faster by forcing it to use more ram. To do this, boot into the usb and open the terminal, type 
```
gksudo gedit /etc/sysctl.conf
```
When the file sysctl.conf opens up, add the line > vm.swappiness=20
vm.swappiness is a parameter that controls how readily the system would use swap instead of ram. It has value between 0 and 100, the higher the value the more readily the system would use swap in place of ram. It slows down the system if you use too little ram. The default value is 60.

The new value for vm.swappiness in sysctl.conf would take effect on reboot. But say you don't want to reboot in the mean time or want to experiment with different values of vm.swappiness before making the change permenant (by editing sysctl.conf) You can change the value of vm.swappiness temporarily and instantly by 
```
sudo sysctl vm.swappiness=20
``` You can try different values between 0 and 100 instead of 20 to find the optimal value before you edit sysctl.conf.

Finally, install bleachbit. Since you have only limited space you would need to clean up junks more often and more throughly.

---

### Post by beew on 2010-12-19
> **lmarmisa said:**
> If you wish an Ubuntu  full installation without modify any Windows partition, consider to use a virtualization type solution. 



A virtualization type solution would definitely modify the windows partition. You have to install a virtualization software like VMware or virtualbox in it! :) OP says he shares a computer so he may not be able to install the virtualization software in the first place.

Moreover I think it is better to work from Ubuntu directly than through an extra layer of virtualization (which may also not be practical for people with not enough ram, for example)

---

### Post by lmarmisa on 2010-12-19
Some people seems to hate virtualization. I really love it. No problem. Different strokes for different folks. :-)

Anyway, I would like to add a comment. According to my experience, an Ubuntu installation on a USB flash drive is not a long term solution. If the virtualization solution is not considered, I would recommend the installation of Ubuntu in an external USB hard drive. Imagine a 500 Gbyte external hard drive. I would define a huge NTFS data partition of about 490 Gbytes (for photos, documents, music, backups, etc) and two small partitions for Ubuntu: for example a 9 Gbytes ext4 partition for root (and everything Ubuntu really) and a 1 Gbyte partition for swap. I would make a full installation of  Ubuntu in this hard drive, writing the GRUB loader in the MBR of this external hard drive. This last detail is important. Even more. If the proprietary graphic drivers are not installed, you will be able to run your Ubuntu system in any computer!. I have several external hard drives with this kind of installations and they work just fine.

---

### Post by C.S.Cameron on 2010-12-19
> **beew said:**
> Hi,

I think you should have at least 8G to consider a full installation. 4G is doable, but it would be very tight.

Also, in addition to C.S. Cameron's excellent step by step tutorial I would suggest that you add a swap partition for about 512M. The windows partition and the /home partition wouldn't be necessary on the other hand IMHO because you are installing on a usb, it is not likely you would store a lot of stuffs there. You only need the windows partition if you need windows to be able access your portable Linux system. I can't really see any reason for that. Your Linux system would be able to access the Windows files in the hard drive when you boot from the usb so if you download something through Ubuntu you would be able to store it in your hard drive anyway.

A problem with full installation in an usb would be speed. It tends to be slow, and a lot slower than a live usb with persistence (which runs in ram) An ideal way to make a portable system would be to install in an external hdd instead. But if you prefer to install in a usb, you can make it faster by forcing it to use more ram. To do this, boot into the usb and open the terminal, type 
```
gksudo gedit /etc/sysctl.conf
```
When the file sysctl.conf opens up, add the line 
vm.swappiness is a parameter that controls how readily the system would use swap instead of ram. It has value between 0 and 100, the higher the value the more readily the system would use swap in place of ram. It slows down the system if you use too little ram. The default value is 60.

The new value for vm.swappiness in sysctl.conf would take effect on reboot. But say you don't want to reboot in the mean time or want to experiment with different values of vm.swappiness before making the change permenant (by editing sysctl.conf) You can change the value of vm.swappiness temporarily and instantly by 
```
sudo sysctl vm.swappiness=20
``` You can try different values between 0 and 100 instead of 20 to find the optimal value before you edit sysctl.conf.

Finally, install bleachbit. Since you have only limited space you would need to clean up junks more often and more throughly.


I like the FAT32 partition in case I want to borrow a MP3 from a friend or want to bring some files home from work.

I never found that I was using any swap space when I had swap and what you can put on a 4GB drive will not allow hibernation.
Also I understand it is better not to write to flash drive unnecessarily. That is why I use ext2, non-journaling, for the home partition.

I use a separate /home partition so I can do fresh installs and not loose stuff.

To each his own, that is what Linux is about.

---

### Post by beew on 2010-12-19
Hi, C.S.Cameron,

I  see your point. While it is true that Linux uses little swap but in my experience (installation in USB) that at least for USB installations it is better to have it and then adjust how much swap you may want to use through manipulating vm.swappiness . It seems that usb installations are more prone to things like freezing, maybe cannot access ram fast enough or something I don't know, I just discovered that it works better with a swap and I can control how much I want to use it in the way I described in my post above.

I don't know how permanently OP wants to use his usb, for a fully functional system I would recommend installation in an external hard drive instead. So I didn't really think about distro upgrade in a usb setting, hence I said a /home partition wasn't necessary (I would recommend it if he installs in an external hdd instead) 


> I like the FAT32 partition in case I want to borrow a MP3 from a friend or want to bring some files home from work.I did both without a fat partition. But then I have permission to boot from the usb in my friend's pc and the computers at work. :) So you may be right there.


> Also I understand it is better not to write to flash drive  unnecessarily. That is why I use ext2, non-journaling, for the home  partition.

Again you are right on this, but my understanding is that for modern usb drives the wear protection technology is much better, the threshold is so high that it is not likely you will kill your usb drive by writing on it too many times if you use it more or less normally.

In any case I wasn't trying to arguing with you. Your tutorial is great   and I wish I had seen it when I first trying to install into external   devices. That would have saved me a lot of searching and hesitation.   Please see this as just additional suggestions. :smile:

---

### Post by candtalan on 2010-12-19
What about grub? When an install takes place onto a removable drive, does not grub still, by default, get put into the removable drive, with mbr pointing to it?

---

### Post by C.S.Cameron on 2010-12-19
> **candtalan said:**
> What about grub? When an install takes place onto a removable drive, does not grub still, by default, get put into the removable drive, with mbr pointing to it?

Judging from posts to the forum if you leave your HDD plugged in and do not use manual partitioning, grub will get put on you removable drive and the MBR on your internal drive will get overwritten. You will need the removable drive to be plugged in to boot your internal one.

This can be fixed using lilo:

[http://ubuntuforums.org/showpost.php?p=10228004&postcount=2](http://ubuntuforums.org/showpost.php?p=10228004&postcount=2)

---

### Post by lmarmisa on 2010-12-19
> **C.S.Cameron said:**
> Judging from posts to the forum if you leave your HDD plugged in and do not use manual partitioning, grub will get put on you removable drive and the MBR on your internal drive will get overwritten. You will need the removable drive to be plugged in to boot your internal one.

This can be fixed using lilo:

[http://ubuntuforums.org/showpost.php?p=10228004&postcount=2](http://ubuntuforums.org/showpost.php?p=10228004&postcount=2)

The install procedure of Ubuntu should be improved, IMHO. In the case of a installation on a removable drive, the GRUB loader should be stored by default in the MBR of that removable drive. This change would prevent a lot of pain for many users.

---

