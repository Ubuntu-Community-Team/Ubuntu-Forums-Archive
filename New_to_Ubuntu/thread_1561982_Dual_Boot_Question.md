---
title: "Dual Boot Question"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by wc5b on 2010-08-27
After installing 10.04, I get two dual boot screens. I have two questions 1. Is there a way to only have one? 2. Is there a way to get it to auto priority Ubuntu vice Windows (I.E. boot to Ubuntu if left unattended)

---

### Post by Deadite81 on 2010-08-27
I'm no expert, but what you describe, although I don't know exactly what you mean, should not be happening.  By default, when you install Ubuntu your boot screen should only appear once and load Ubuntu by default, not Windows.

If you have not attempted to tweak anything, the fix should be simple.

First you could try typing "sudo *update*-grub" (no quotes) into a terminal. (Applications -> Accessories -> Terminal in your menu.) All that does is update your boot loader's config file, I don't know that it would fix you problem, but it's worth a shot.

If that doesn't work, this is a more likely solution. Go to Administration -> Synaptic Package Manager in your main menu.  Search for "grub".  You should see a few items with green squares next to them.  Namely "grub-pc" and "grub-common".  

Right-click them both and choose "Mark For Reinstallation".  Click the "Apply" button.  It will reinstall the packages, and it should stop and ask you if you want to replace the configuration file.  Answer yes, you do want to replace it.  (It may do this automatically.)

If that doesn't fix it, you can try and completely remove them and then reinstall them.  If that doesn't work the problem is deeper.  Please note that you have to have grub installed to boot your computer, so be careful!

---

### Post by wilee-nilee on 2010-08-27
Wait is this a wubi install=from a live windows environment? 

If that is the case as far as I know, you need the MS bootloader to load MS or to chainload Ubuntu, so 2 bootloaders.

If this wubi your grub setup is different then a normal install so never update it or install to a partition or the mbr.

---

### Post by Deadite81 on 2010-08-27
Ah, I did not consider Wubi!  If this is the case do not follow my advice because I know nothing about Wubi!  (Seems kinda pointless to me unless you're just checking Ubuntu out to see what it's like.)  If this is the case I apologize.  I should have asked more questions first since your description was sort of vague.  Thanks for spotting that @wilee-nilee.

---

### Post by wc5b on 2010-08-27
Ya, I did use WUBI install, and that is what I am referring too. It appears to have a MS GRUB and then a UBUNTU GRUB.   Anyway to get rid of the MS?  or at least get it to priority the Ubuntu side. Right now if I start computer and walk away, the first MS GRUB would time out and start windows.

---

### Post by Cavsfan on 2010-08-27
Check out the tutorial in my signature. It will do what you want.
EDIT: My bad. If you do a regular install first. Then you could use the tutorial.
I dual boot Ubuntu x64 and Windows 7 x64

---

### Post by LinuxFox on 2010-08-27
> **wc5b said:**
> Ya, I did use WUBI install, and that is what I am referring too. It appears to have a MS GRUB and then a UBUNTU GRUB.   Anyway to get rid of the MS?  or at least get it to priority the Ubuntu side. Right now if I start computer and walk away, the first MS GRUB would time out and start windows.There is a way with Wubi.  Boot up Windows.  After Windows boots up, right click My Computer and choose Properties.  Open up the Advance Settings and in there should be Startup options.  Open the Startup options, and change the Boot priority from Windows to Ubuntu.  Apply and click OK.

This won't get rid of Windows, but it will set Ubuntu to boot first.  I did this to my mother's computer as I used Wubi to give her less problems.

---

### Post by wc5b on 2010-08-27
AWSOME!! I guess worst case I could reduce the time out of the second. Thanks.

---

### Post by oldfred on 2010-08-27
Wubi is fine for trying out Ubuntu on a longer basis than that of using a liveCD but is not intended for long term use. If you are to the point of liking Ubuntu enough to regularly use it you should consider converting to separate partitions. Even the designer of wubi expects users to convert to partitions:

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

The old conversion LVPM does not work, see Alternative Instructions, but I believe bcbc has update a script to work.
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by wc5b on 2010-08-27
OK, so If I use the walkthrough you link, I still need to somehow partition a chunk of NTFS off. Not sure I remember if thats even possible. I am trying to keep the windows install active since I MUST use Microsoft Office for educational requirements.

---

### Post by wilee-nilee on 2010-08-27
> **wc5b said:**
> OK, so If I use the walkthrough you link, I still need to somehow partition a chunk of NTFS off. Not sure I remember if thats even possible. I am trying to keep the windows install active since I MUST use Microsoft Office for educational requirements.

Kind of cryptic what is it that you really want now.;)

---

### Post by wc5b on 2010-08-28
Actually, after learning more about this type of install, I have decided to just wipe the system and install a full version using an ISO. I just need to get MS OFFICE 2007 running under WINE as an educational institutions requirement. I have got the WORD running which is most important, just need to tweak EXCEL and POWERPOINT. I am sure I will get it figured out with the help of the community here. Thanks for your help.

Tom

---

### Post by Cavsfan on 2010-08-28
I am probably too late to mention this, but I was going to say that in windows (I have windows 7) 
you can open Disk Manager and "shrink" the C: drive to possibly free up enough space to install Ubuntu on.
You can search for it "Disk Manager" in windows. That is how I freed 100GB for my install.

---

