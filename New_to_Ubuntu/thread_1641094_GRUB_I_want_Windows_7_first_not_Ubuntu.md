---
title: "GRUB: I want Windows 7 first not Ubuntu"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by badgerdisco on 2010-12-08
Hi all

I have recently dual-booted Ubuntu (10.10) onto my computer alongside Windows 7.

I must admit I'm more and more impressed with Ubuntu everyday I use it however, I was very annoyed that Ubuntu replaced my windows boot loader with GRUB. 

As a beginner, the GRUB menu is horrible, the messy list of things doesn't really make any sense to me, all I want to see is Windows 7 and Ubuntu beneath it! 

Can anyone help me set it up so Windows 7 boots first (is at the top of the list) 
I have tried to do this by following some online stuff, but when I run this command:

sudo gedit /boot/grub/menu.lst

There is no list, just a blank file!?  Ideally, I'd rather just use the Windows boot loader, but don't mind the GRUB if I can change the order! 

Thanks for your help!

---

### Post by Quackers on 2010-12-08
Grub is better than the Windows bootloader for several reasons that I won't go into now. 
For a short term fix you can install Startup Manager via Synaptic Package Manager and set the default boot OS there.
If you want to tidy up the grub menu and set Windows 7 as the default option all is revealed here 

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

and here

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

and here

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by badgerdisco on 2010-12-09
Thanks Quackers.  I have nothing against GRUB I just preferred the simple display off the Windows one, as a Windows user my entire life, it's going to take time to adjust to Ubuntu! 

Thanks for your advice regarding the Start-Up Manager, I managed to find some info online and got that to work, it's a good fix! 

As for the other information you presented, I'm going to need to do some more reading as it's quite confusing to a beginner like myself. 

Thanks though, problem one sorted with help of this forum!

---

### Post by Quackers on 2010-12-09
Yes, it can look a bit difficult. Take your time and get used to using commands in the terminal first. There's no rush :-)
Enjoy!

---

