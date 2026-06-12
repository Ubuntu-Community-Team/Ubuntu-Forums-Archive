---
title: "Need Help With Booting Vista"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Rey117 on 2010-03-16
My fiance recently decided to switch over but once we did everything linux was working but however when I go and load vista it wont load after I selected from GRUB...I click on it and it seems to start up then but stop during the boot or it brings me up to the recovery screen and i select fix automatically and it says it does and it restarts but it doesnt do anything...What should I do?

---

### Post by Rey117 on 2010-03-16
Bump

---

### Post by andrewthomas on 2010-03-16
> **Rey117 said:**
> My fiance recently decided to switch over but once we did everything linux was working but however when I go and load vista it wont load after I selected from GRUB...I click on it and it seems to start up then but stop during the boot or it brings me up to the recovery screen and i select fix automatically and it says it does and it restarts but it doesnt do anything...What should I do?
Do you have a Vista DVD?  If you do, boot from it and select the repair option.

---

### Post by Rey117 on 2010-03-16
Nope she doesnt have it plus the repair option comes up anyways when i try to boot it and nothing

---

### Post by oldfred on 2010-03-16
Boot from the Windows CD as before. But instead of choosing "Startup Repair" choose "Command Prompt". Then

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)

---

### Post by nmaster on 2010-03-16
> **oldfred said:**
> Boot from the Windows CD as before. But instead of choosing "Startup Repair" choose "Command Prompt". Then

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)

i've never had to do it, but i hear that the neosmart links are the way to go.  it sounds like you may have used gparted to resize your partitions instead of the tool included in Vista.

---

### Post by NightwishFan on 2010-03-16
Vista will refuse to boot if it does not like how you resized the disks. I always advise to use built in tools for doing so. You will likely need a recovery disk to repair.

---

### Post by julio.tomaschitz on 2010-03-16
I had some trouble with (bad)vista when I had installed ubuntu on it. I discovered that there is some "magic" on vista partition, and just the windows partiotioner can resize the disk, then, if you want to use the gparted or something, you'll have some problems...

Thats doenst occour on XP, so, is better you change to XP, or only put ubuntu.

I backed up my vista files using ubuntu, and formatted that partition, after, installed XP and its drivers.

Oh well, dont forget the drivers before installing XP! or you wont have network, nor have access to ubuntu, cause windows installation destroy it.

---

### Post by Rey117 on 2010-03-17
OK I Burned the CD now what do I do?

---

### Post by dreamsburnred on 2010-03-17
> **Rey117 said:**
> OK I Burned the CD now what do I do?
Put in the computer, and boot from it (boot options at start up).

Do repair startup.

I've personally had to do it 3 times in a row before Vista would wake up.

---

### Post by Rey117 on 2010-03-17
Do you know if I will lose any data on the user profiles?

---

### Post by Rey117 on 2010-03-17
> **oldfred said:**
> Boot from the Windows CD as before. But instead of choosing "Startup Repair" choose "Command Prompt". Then

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)
I open command prompt then what?

---

### Post by Rey117 on 2010-03-17
Bump

---

### Post by Rey117 on 2010-03-17
Bump

---

### Post by coffeecat on 2010-03-17
> **Rey117 said:**
> I open command prompt then what?

Personally, I would choose 'startup repair' first. You might need to run this more than once. If you're really stuck, then do have a go with the command prompt. Here's a guide which might help:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Note that it says:

> **Note **When you are troubleshooting startup issues by using the  Windows RE, you should first try the **Startup  Repair** option in the **System Recovery  Options** dialog box. If the **Startup  Repair** option does not resolve the issue, or if you must  troubleshoot more steps manually, use the Bootrec.exe tool.If you do use the command prompt, don't use the fixmbr command. That will overwrite grub stage 1 on the MBR and you won't be able to boot into Ubuntu without repairing grub.

---

### Post by Rey117 on 2010-03-17
Well I tried to do it through the Command Prompt and managed to destroy GRUB and and cant load Vista....Would it be better just install windows 7? then how would i get GRUB back?

---

### Post by NightwishFan on 2010-03-17
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That link will explain the process in recovering grub.

---

### Post by coffeecat on 2010-03-17
> **Rey117 said:**
> Well I tried to do it through the Command Prompt and managed to destroy GRUB and and cant load Vista....

You ran fixmbr, didn't you? I warned you not to.

> **Rey117 said:**
> Would it be better just install windows 7?

Probably.

> **Rey117 said:**
>  then how would i get GRUB back?

Read this:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you need help interpreting those instructions when you get to reinstalling grub, I suggest you start a new thread with a title appropriate to reinstalling grub and post the output of...

```
sudo fdisk -l
```You'll have to do fdisk using the live CD.

---

### Post by Rey117 on 2010-03-17
Hahaha I'm having the time of my life to trying to fix this so I formatted the HDD and i tried to load up Window 7 ultimate but when i boots up from the flash it stops at the effing command prompt and i don't know what to do about it..and about the grub eh thats the least of my worries I just want to get some form of windows up for my fiance...

---

### Post by tommynz1975 on 2010-03-17
I do not want to confuse the current help given.   But what seemed to work for me was this.... I let ubuntu part my vista Hard Drive because I knew no better.

What fixed it was to hit "F2" after having selected to boot vista from the grub.
This brought up a  menu with 2 options
Boot Normally
Tools
I chose Tools and let it do its thing.

For some reason having gone through this exercise made windows boot.
I do not know if I was just lucky or what?

Best of Luck.

---

### Post by Rey117 on 2010-03-17
As of right now I can't boot anything..

---

