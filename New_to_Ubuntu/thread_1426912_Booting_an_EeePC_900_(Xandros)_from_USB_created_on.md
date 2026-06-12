---
title: "Booting an EeePC 900 (Xandros) from USB created on a Mac"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by LinuxRR247 on 2010-03-10
Good evening all, 

I am at my wits end.  I am very new to Ubuntu, and really *_REALLY_* want to install it on my EeePC 900 (which runs ***yuck*** Xandros...).  

I downloaded the UNR 9.10.iso file onto my Mac Mini (Intel), and followed the instructions found here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick).  In the Source Computer section, under the Mac heading, there are several bullets outlining steps to be taken in the Terminal.  I had an initial problem because the syntax of the third bullet was a little confusing, but eventually I got it to work (I think).  I checked the MD5 checksum of the .iso file I downloaded and it was correct, so I'm pretty sure I used a clean .iso file to convert to the .img file.  Now to the issue: 

I changed my BIOS settings on the EeePC 900 to check for removable media first, then restarted and held down ESC, getting the proper pop-up to choose the Removable Media drive to boot from.  The problem is that my USB 'blinks' for about a second, then the LED goes out and the EeePC boots from the SSD into Xandros!  Gah!  *NOT* what I want!  

I did a search on "EeePC 900" and "Boot" on this forum and there were several suggestions, ranging from 'use a different USB drive' to 'try to boot from the USB drive after exiting BIOS'.  Nothing works.  When following the instructions noted above, the last bullet asks me to restart my Mac, while holding down Alt.  What does this do?  I tried it and all I got was a grey screen with an icon for my HD, no USB, nothing else.  My mouse wouldn't work, but if I hit enter, then the Mac booted from the HD.  So, I'm totally confused now.  

I apologize for the novel above, but I've done my research and just can't seem to figure out a way around this issue.  Thank you very much for any and all help, it is really appreciated!!  

LRR

---

### Post by LinuxRR247 on 2010-03-11
-bump-

Evening all...no more progress...

So I'm trying it again from the "Installation/FromUSBStick" instruction page.  I went through all the steps again, and this time I used a Sony Microvault 4GB drive.  I get the same behavior on my EeePC 900...the LED blinks on the thumb drive, then the system goes straight into booting up Xandros from the SSD.  

The .iso file I downloaded is the correct file, I think, and it isn't corrupted.  Is there a way to boot the Mac as a Linux machine and try the Linux instructions?  I am a little frustrated and thus throw myself on the mercy of the experts in this forum.  

Asus EeePC (20GB model running Linux).  BIOS version 0501, BIOS date: 05/12/2008, software version Eee PC 1.1.0.66.  If any more information is needed, I will gladly provide it!  Thank you! 

LRR

---

### Post by alfplayer on 2010-03-11
If your mac can boot a Ubuntu Live CD you can try the "recommended way" as suggested in [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by barrieluv on 2010-03-12
What steps are you taking to prepare the thumb drive before putting the .img or .iso onto it?  Forgetting to format the entire drive properly, including any hidden partitions containing the manufacturers software, nd not flagging the drive bootable are the usual culprits in these cases.

As alfplayer suggested, you coud boot your mac using a live Ubuntu cd and create the bootable drive from there...

---

