---
title: "Dual boot problem with Windows and Ubuntu across 2 drives"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by skinks on 2009-12-13
I previously had Win XP on IDE drive and Ubuntu on Sata drive (much newer drive with 10x more space). I used GAG boot up manager to load either operating system and it worked great. However, recently I had error with driver which caused Ubuntu not to load. I've now reloaded Ubuntu with success. However, the dual boot using GAG no longer works!
 
Here is what I have: 30 GB IDE drive with Windows XP installed. 300 GB Sata drive with Ubuntu (here I have 90MB partition setup as /boot, 30GB as /, and remainer as /home). The BIOS goes to IDE drive and boots up whatever is there. With GAG installed previously, it replaced MBR on IDE drive, and it always booted Ubuntu when I pointed GAG to the /boot partition on Sata drive. Now, after Ubuntu re-install, I get the GAG error "sector boot not found or invalid" when I try and point GAG to /boot partition, exactly as I did before!
 
When I unplug the IDE drive, the BIOS boots up Grub and Ubuntu works fine. But, this is not good solution. Unfortunately I still have to run Windows only for iTunes and Quicken, so I need the Dual boot option.
 
Anyone know how fix this GAG - Grub problem?? Any other ways to dual boot on multiple drives - Windows and Ubuntu??

---

### Post by Redache on 2009-12-13
Have you tried reinstalling GAG? I have no idea what GAG is so I can't help you with configuring it.

---

### Post by skinks on 2009-12-14
GAG is a graphical boot loader.  It installs in the MBR of the primary hard drive.  It did great on first install of Ubuntu.
 
Yes, I did already try an uninstall and install of GAG.  I got the same error message.  So, for some reason this Ubuntu install of the boot paritition is not recognized by GAG graphical boot loader.  
 
I'm at a loss on what to do next.  If there are other ways to dual boot across mulitple drives, I'd like to konw.

---

### Post by steve-shinn on 2009-12-14
Are you running Ubuntu 9.10 by any chance ? If so this version of Ubuntu now uses grub2 which does not use menu.lst. Maybe this is the issue.

---

### Post by skinks on 2009-12-14
I have not upgraded to Ubuntu 9.10 yet.  Boot up is definitely using the menu.lst file for I had to make a correction in the boot file path names to get the boot to work with primary IDE drive unplugged.  
 
When I installed Ubuntu on SATA drive, I unplugged the primary IDE drive to avoid any conflicts on booting up Ubuntu.  Should I have kept that drive plugged in so that Ubuntu install would recoginze the Win XP OS residing there?  
 
The boot partition has to be configured differently than it was before.  Before the GAG boot up program recognized the boot partition correctly, and I had no problem.  Now it does not, even though I'm installing exactly the same way as previous.  
 
It's annoying trying to get this Dual boot to work.  It took a lot of work on first Ubuntu install, and now on 2nd install, it looks like it'll take even more work!

---

### Post by ukripper on 2009-12-14
Why you using GAG and not GRUB to write entries to MBR?

As you are still using Grub 1 not grub 2 you can use supergrubdisk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by skinks on 2009-12-14
I'm using GAG as I could never get the GRUB to work as the boot loader for dual boot the first time I installed Ubuntu.  It worked for fine for Ubuntu but never worked for booting Windows.  GAG was only solution that worked.  I will try the supergrub and see if I can get Grub to work this time around.

---

### Post by bumanie on 2009-12-14
I am yet to use GAG, but think it right to point out that it does not install in the mbr, it actually sits on the first track of the hard drive where there otherwise is nothing written. To fix, I would try to purge your present version of GAG and then reinstall it - but as said, I haven't used GAG, although am interested in trying it - so what I have suggested is a bit of a guess. Grub-legacy often had issues with mixed ide and sata drives, which may be the root of your problems with dual booting - grub2 should handle that scenario better.

---

### Post by skinks on 2009-12-16
Just when I solve one problem, another one pops up.  For dual boot, I gave up on GAG, and I tried the supergrubdisk as recommended in this thread.  I ran it on Windows side.  Program installed, ask for reboot, then came up with grub list with choice of Ubuntu or Windows.  I selected Ubuntu.  It failed to start... Error 15 again.  I rebooted and this time it went straight to booting Ubuntu 9.04.  Strange.  I restarted again, and pressed ESC to get to Grub menu.  The choice for booting up Windows is gone!  Now I'm stuck again.  Ubuntu is booting  but I can't figure out how to get back to having choice of Windows or Ubuntu at boot up.  I still need Windows occasionally until I can figure out iTunes and Quicken workarounds.  Now what to do?  

I've considered 9.10 upgrade with grub2.  But, I just assume I'll be trading one problem for another.  This dual boot has been very frustrating on my PC with one 1 primary IDE HD and a secondary SATA HD.

---

### Post by kansasnoob on 2009-12-16
Well, to truly troubleshoot this and find an actual solution lets have a look at the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

**Note:** whatever solution I come up with will **not** include GAG.

---

### Post by ukripper on 2009-12-17
> **skinks said:**
> Just when I solve one problem, another one pops up.  For dual boot, I gave up on GAG, and I tried the supergrubdisk as recommended in this thread.  I ran it on Windows side.  Program installed, ask for reboot, then came up with grub list with choice of Ubuntu or Windows.  I selected Ubuntu.  It failed to start... Error 15 again.  I rebooted and this time it went straight to booting Ubuntu 9.04.  Strange.  I restarted again, and pressed ESC to get to Grub menu.  The choice for booting up Windows is gone!  Now I'm stuck again.  Ubuntu is booting  but I can't figure out how to get back to having choice of Windows or Ubuntu at boot up.  I still need Windows occasionally until I can figure out iTunes and Quicken workarounds.  Now what to do?  

I've considered 9.10 upgrade with grub2.  But, I just assume I'll be trading one problem for another.  This dual boot has been very frustrating on my PC with one 1 primary IDE HD and a secondary SATA HD.

ok boot into your ubuntu and post output of this command:
```
gedit /boot/grub/menu.lst
```

---

### Post by skinks on 2009-12-18
Thanks kansasnoob!  That is a great script to run and diagnose boot problems.   I was able to identify which drives and partitions have boot information on them.  And then I was able to add to menu.lst as shown below.  Problem solved on boot.  I would change this thread to [SOLVED] but I do not know how.

I finally understand the menu.lst and grub.  I'm reluctant now to go with Version 9.10 anytime soon for I hear it uses grub2 which has no menu.lst.  I'm sure again I'll have boot problems when I upgrade.  But, I'll have Ubuntu Forums to help me fix that problem!

title        Windows XP
root        (hd0,0)
makeactive
chainloader +1

---

