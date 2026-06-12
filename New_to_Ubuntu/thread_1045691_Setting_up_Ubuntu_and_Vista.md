---
title: "Setting up Ubuntu and Vista"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Scott_MacAdam on 2009-01-20
Hey everyone!

I'm in need of some help here.....

I switched to Ubuntu a couple of months ago and everything is working fine, but I'm wondering how I can also have Vista installed on my PC so I can switch back and forth. I have heard of a few options such as having them both installed on my internal harddrive, having Linux boot off of a thumb drive, having one installed on my external harddrive and so on but i would know where to start or which one would work best.... 

I've got a disk for Ubuntu 8.10 (which I am currently running as my OS)
I've got an ISO for Vista and a patcher.... (should I burn this or mount it)

Can someone make a suggestion on how to take this on?

Thanks a lot

---

### Post by Tatty on 2009-01-20
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

This guide will take you through setting up a dual boot.  

The only thing to add is that since you are using vista, it may be better to shrink the size of your vista partition using vista's own partition editor.

---

### Post by kansasnoob on 2009-01-20
> **Scott_MacAdam said:**
> Hey everyone!

I'm in need of some help here.....

I switched to Ubuntu a couple of months ago and everything is working fine, but I'm wondering how I can also have Vista installed on my PC so I can switch back and forth. I have heard of a few options such as having them both installed on my internal harddrive, having Linux boot off of a thumb drive, having one installed on my external harddrive and so on but i would know where to start or which one would work best.... 

I've got a disk for Ubuntu 8.10 (which I am currently running as my OS)
I've got an ISO for Vista and a patcher.... (should I burn this or mount it)

Can someone make a suggestion on how to take this on?

Thanks a lot

My preference would be a dual boot:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by Scott_MacAdam on 2009-01-22
Great info there! 
Thanks a lot!

Can someone tell me which way would be the easiest to do? my computer and I are a bad team for messing things up and honestly, the easier and more basic the steps the better the chance of me not messing it all up and having to wipe the harddrive yet again.....

I'm using UBUNTU now, but I could just back up what want to keep to and put windows on first then add ubuntu back if it would be easier in the long run.... I'm pretty terrible at coding things....

---

### Post by caljohnsmith on 2009-01-22
If you can create a new primary (not logical) NTFS partition for Vista, you shouldn't need to wipe the HDD and install Ubuntu afterwards. Try installing Vista to the primary NTFS partition you create, and then once you are done, you can get Grub back by following [these directions]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). Or you could follow the tutorial that kansasnoob linked to, because it says basically the same thing. Then all you would need to do is add an entry for Vista in your Grub menu after you are done installing Vista and restoring Grub. If you would like some help with that, how about posting:
```
sudo fdisk -lu
```
After you are done with installing Vista, and we can work from there if you want.

---

### Post by TJCIB on 2009-01-22
To be perfectly honest, IMO the BEST way to do a dual boot is to have two separate hard drives.  I think it saves a lot of headaches and loss of data.

Depending on the sizes of your hard drives, it is pretty easy to set up.  Ubuntu doesn't need much space to run, and 20GB hard drive is PLENTY of space to have as a second HD and install Ubuntu.

Just my opinion.

---

