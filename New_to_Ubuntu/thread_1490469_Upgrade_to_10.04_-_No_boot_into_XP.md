---
title: "Upgrade to 10.04 - No boot into XP"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by rayoung02 on 2010-05-22
I just upgraded to 10.04 from the previous release and I've had a couple annoying issues so far:

At the Grub screen when you first start up it won't boot into Windows XP. It shows that it's there, but when I try booting it there is just a black screen with a flashing dash in the top left screen. I'm using Grub 2. I ran boot info script and got this:

File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1836826982 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

I'm pretty new and not quite sure what to do next. Thanks

---

### Post by bcbc on 2010-05-22
See [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by rayoung02 on 2010-05-22
Thx man that worked!

---

### Post by bcbc on 2010-05-22
Great... you're welcome :)

Feel free to add a comment to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724"). The more people that 'add input' the more likely someone will do something about it.

---

