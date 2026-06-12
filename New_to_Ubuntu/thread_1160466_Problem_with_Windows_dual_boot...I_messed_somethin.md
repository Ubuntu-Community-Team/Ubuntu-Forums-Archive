---
title: "Problem with Windows dual boot...I messed something up"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by raj9786 on 2009-05-15
Ok so I was having some trouble with the installation from the LiveCD so I tried the alternate CD. One of the options in the alternate cd was to install grub onto /dev/sda or something like that. The problem is, i for some reason thought it was a good idea to install it on /dev/sda1 (which i assume is my windows partition). So that did not work and so i reinstalled, now with grub on the correct /dev/sda. the problem is that while ubuntu works fine, I cannot boot into windows anymore. I can access the windows partition through ubuntu though. Is there any way I can take grub off of sda1 to get my windows up and running? ive tried a bunch of things including overwriting the bootloader etc but im assuming that just overwrites the correct grub installation and not the errant on on sda1. Any suggestions? Thank you very much

---

### Post by Mortus Pryde on 2009-05-15
Are you getting any sort of an error when you try to boot to Windows?

---

### Post by logos34 on 2009-05-15
if you have XP, you need to run fixboot command (either from the recovery console on the XP install cd, or use Super Grub Disk--see link below)

---

### Post by reg4c on 2009-05-15
Try re-installing GRUB from a LiveCD.

---

### Post by sundar_ima on 2009-05-15
as logos said super grub disk is the best option...

---

### Post by raj9786 on 2009-05-16
So i've tried using the super grub disk. i think ive tried almost every option on it but i get errors on some of them. I can try a specific command and post the output if you think that will help.

During startup, when i select the windows partition to boot up, a screen comes up that says "Starting up..." and it just sits there. Not sure what else to do at this point although I am a noob so that may not mean much haha. Thanks.

---

### Post by logos34 on 2009-05-16
according to the info in your initial post, looks like you overwrote the windows bootsector code on sda1...so going through the 'fixboot' steps in Super Grub Disk should fix that. Did you do that or just try to use SGD to boot windows?

---

### Post by raj9786 on 2009-05-18
stupid question. how exactly do I use the fixboot command? do i need to go into the command line? what is the syntax of the command i need to input? thanks guys.

---

### Post by logos34 on 2009-05-18
if using the xp cd, you'd do 'R' for recovery console, then at the commandline prompt type

fixboot

If using Super Grub, you navigate to the ['Windows' menu entry]("http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems")...there's an option to fix the boot (NOT fixmbr, because that will overwrite grub bootloader!)

sorry, can't find the exact SGD wiki page...a lot of stuff there is still on 'TODO' list

---

### Post by raj9786 on 2009-05-18
so in SGD when using the WIN => MBR & !WIN! :((((((((((((((((( option i get the following output

set aux_hd="hd0"
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0 0 300
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0x1fe 0x1fe 2
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

and it just sits there after the boot command. is that useful information for my problem? thanks

---

### Post by logos34 on 2009-05-18
I haven't used it in ages...you might look under 'WINDOWS (Advanced)' or 'Misc' menu entry:

> 
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#How_To_Use_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#How_To_Use_Super_Grub_Disk)

Windows (Advanced) leads to a menu where you can
restore Window's NTLDR bootloader's IPL to MBR (equivalent to FIXMBR),
boot Windows by its boot sector (bypassing the MBR),
boot Windows on a non-first hard disk,
set the boot flag on a Windows partition,
and
**re-install Windows NTLDR's IPL to a boot sector (equivalent to FIXBOOT).**

...

Miscellanea give you a menu for selecting to boot your Linux installation or fix a Windows boot sector (equivalent to FIXBOOT).

---

### Post by raj9786 on 2009-05-20
Tried the Fix boot command. no dice. it just uninstalled grub.

---

### Post by chubby127 on 2009-05-20
Raj, I did basically the same thing you did. I had XP installed on my pc and attempted to install jaunty on it. The instillation was fine up until the final screen (where it asks where to install GRUB) and i stupidly chose sda1 (which is where XP was). After restarting, GRUB would load and jaunty worked fine, but when i tried to boot into XP it just hung. However, I couldn't access my windows partition from ubuntu because for some reason GRUB had formatted the windows parition without any warning it was doing so. Thus, I had to run testdisk and photorec and waited about 7 hours to get some of my files back that were formatted on the partition. You're lucky you can still access your files, I got f***ed. I would definitely backup your windows partition as soon as you can just to be safe.

---

### Post by logos34 on 2009-05-20
> **raj9786 said:**
> Tried the Fix boot command. no dice. it just uninstalled grub.

I don't understand how that happened...The 'fixbmr' function would do that (overwrite grub on the mbr), but the 'fixboot' command by contrast should restore the windows bootloader code to the first sector of the windows C: partition (which you mistakenly overwrote with grub during installation).  Hmm...

I hoped you could avoid using Testdisk because its kind of drastic, but I guess you have no choice but to use it in this case, if only to fix the windows bootsector.  Read [this step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery") ['NTFS Boot sector recovery']

sudo apt-get install testdisk

sudo testdisk

---

