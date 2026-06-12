---
title: "Grub error for Ubuntu 9.10 installed on Inspiron 1545."
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Coolcat310 on 2010-02-01
I've recently installed Ubuntu 9.10 32-bit on my Dell Inspiron 1545 with Windows 7. The Grub boot loader worked fine for awhile. I changed the default settings in /etc/modprobe.d/grub and updated it to boot into Windows 7 first. Still worked. Then, the other day Grub gave me an error saying "Mulloc" not found. So I followed the Grub2 reinstall guide from a Live CD.
 
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
 
# Rebooted the computer, Grub loaded to Ubuntu fine.
 
[FONT=Courier New]sudo update-grub[/FONT] 
 
After this, Grub would work fine again for awhile, then would give me the same error as above. Am I doing something wrong?

---

### Post by meierfra. on 2010-02-01
Sounds like some Windows program corrupts your MBR.  Check out this link
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

If you like more detailed help, follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to run the boot info script and post the RESULTS.txt

---

### Post by Coolcat310 on 2010-02-01
Thanks for the quick reply.  Would you recommend a certain solution? What does* "Solution* 4 Install Grub2 to the MBR without embedded core" mean exactly?  What's the embedded core do?
 
For the boot script, do I run it after the problem occurs or whenever?
 
Thanks again and will try one of the solutions.

---

### Post by meierfra. on 2010-02-01
> For the boot script, do I run it after the problem occurs or whenever?
Whenever. But you might as well do it now.

> Would you recommend a certain solution? 

I vote for Solution 1 (figuring out  what program is writing to the MBR, and disable it. ) That way you get to keep Grub 2, and it would also be useful for anybody else running into the same problem.
But unless  you have one of the already listed programs, Solutions 1 is the most difficult one, and you might have to wait until the next time your computer  runs into problems to get some real evidence.

Solution 2 (reverting the legacy grub) is probably the easiest one. And it should work in most case.

Solution 3 (using a different boot loader) I would only recommend if  neither 1, 2 or 5 work

Solution 4 (install grub2 with embedded core)  should solve your problem, and you get to keep Grub 2. But it means that  Grub2 will only use the first sector of your hard drive, and won't be able to look for the grub.cfg by its name. Instead it will look for the file core.img in /boot/grub by its physical location. Unfortunately  this location can  change during kernel updates, and Grub 2 cannot be configured to automatically update the MBR under these circumstances.  So you would have to reinstall Grub after each kernel update.  Thus I wouldn't recommend this solution

Solution 5:  (installing Grub2 to a different hard drive) If you have a second hard drive and can switch the boot order in the bios, this is a very easy and very good solution (although sometimes booting can be slow)

---

### Post by Coolcat310 on 2010-02-01
Ok, here's my results from the script.  Does that mean that the "Dell Utility" is in the same sector as the MBR?

---

### Post by meierfra. on 2010-02-01
> "Dell Utility" is in the same sector as the MBR? 
No. The Dell Ultility partition starts at sector 63.  Grub is installed in the sectors before that.


Let me know if you are willing to try Solution 1.  

 But if you rather  go for the quick and easy solution, these are the instruction to revert to Legacy Grub:

```
sudo apt-get purge grub-pc
sudo rm /boot/grub/*
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
sudo update-grub

```
Say yes when asked to generate "menu.lst"

The open menu..lst via
```
sudo gedit /boot/grub/menu.lst
```
Add the following to the very end of the file:

title Window 7
rootnoverify (hd0,2)
chainloader 1

Save the file. Reboot and see whether you can boot into both OS's

---

### Post by Coolcat310 on 2010-02-01
At first, I tried solution 2 so that I could get it to constantly boot.  But wanted to know exactly what was causing it so I reinstalled Grub2 and proceeded with Solution 1.  I did have the Dell DataSafe Local Backup and uninstalled it.  I did run into some problems when restarting as I couldn't boot anymore using a LiveCD, but I had installed Ubuntu on a USB drive as well, so I used that to boot.  I got Grub to work again and rebooted into windows.  And I've gone back and forth between Ubuntu and Windows 7 and still working.  

Thanks for all your help.  I'm sure I'll need it again :D

---

### Post by meierfra. on 2010-02-01
> And I've gone back and forth between Ubuntu and Windows 7 and still working. 
Great.   Let's us know if the problems reoccurs.

---

