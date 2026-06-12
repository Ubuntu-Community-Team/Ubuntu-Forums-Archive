---
title: "Can't open ISO at a new bought computer"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by reinehrdotorg on 2008-12-07
Sorry for this sooo basic question, but I bought a brand new computer with no operational system on it and I really want to start Ubuntu from Zero.

I've downloaded Ubuntu 8.10 from the site and created a CD with Nero but, even booting from CD/DVD i'm not able to get it installed, since a message telling "No bootable device was found. Please insert a valid bootable device and press any key" appears

And now I'm stucked. Don't know where to run. Any suggestions?

---

### Post by scragar on 2008-12-07
In your BOIS check the boot order, make sure it boots from CD.

I'd also check the CD for errors.

---

### Post by Rocket2DMn on 2008-12-07
Did you burn the ISO as an image or as raw data?  The ISO needs to be burned as an image, and then the cd drive has to be in the boot order in the BIOS as scragar mentioned.  Usually when you boot a computer there is an option at the first screen to enter the BIOS and another to enter a boot menu.  You usually only have a second or so to make the selection, so you may need to try a few times, but if you enter the boot menu, you should be able to select to boot from the cd without fiddling around in the BIOS.
For more information, please see:
[uhelp]community/BurningIsoHowto[/uhelp]
[uhelp]community/HowToMD5SUM[/uhelp]
[uhelp]community/UbuntuHashes[/uhelp]

---

### Post by cartisdm on 2008-12-07
Will the CD boot on other computers? It's possible it wasn't burned correctly

---

### Post by reinehrdotorg on 2008-12-07
I'll try to see if it was burned correctly. Thanks for the prompt help!

---

### Post by ugm6hr on 2008-12-07
Follow the advice here: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

If the CD doesn't boot, either you burnt the CD as a file rather than as an iso or you've not set the BIOS to boot from CD correctly.

---

### Post by reinehrdotorg on 2008-12-07
Thanks a lot! I was I totally dumbass and couldn't get Nero to burn an ISO file. So i've downloaded ISO Recorder and get all thing to order!

Now I'll move on to find the drivers to my brand new Ubuntu!

Thanks to everyone!

You (and the software) are awesome! This forum is the most fabulous thing I've ever seen!

---

### Post by Zill on 2008-12-07
> **reinehrdotorg said:**
> ...Now I'll move on to find the drivers to my brand new Ubuntu!...

Linux is not Windows!  You shouldn't need to search for drivers - in Linux they are generally installed by default :-)

Just stick your ISO cd in the drive and reboot.  Try to run the live CD and if this runs OK then simply click the install icon on the Ubuntu desktop to install it to your HDD.

---

### Post by cartisdm on 2008-12-07
> **reinehrdotorg said:**
> Thanks to everyone!

You (and the software) are awesome! This forum is the most fabulous thing I've ever seen!

Aw shucks, you're making us blush:redface:

Stay in touch with the forum, you'll benefit greatly from everyone here.  I know I certainly have!

---

### Post by reinehrdotorg on 2008-12-07
The Saga continues! hehe! Let's see if I can move on: after installing everything perfectly (without errors) I was asked to remove installation CD and restart. OK, fine.

Then, a message appears: 

GRUB Loading Stage 1.5

GRUB Loading, please wait...
Error 2

And i'm stucked at this point. And now, where do I go?

---

### Post by reinehrdotorg on 2008-12-07
The Saga continues! hehe! Let's see if I can move on: after installing everything perfectly (without errors) I was asked to remove installation CD and restart. OK, fine.

Then, a message appears: 

GRUB Loading Stage 1.5

GRUB Loading, please wait...
Error 2

And i'm stucked at this point. And now, where do I go?

---

### Post by Rocket2DMn on 2008-12-07
That means that grub can't find the hard drive or partition that it believes Ubuntu is supposed to be on.  I suggest reinstalling GRUB rather than just trying to fix it, tbh it's easier.  I like to use the Super Grub Disk - [http://supergrubdisk.org/](http://supergrubdisk.org/) - just burn the ISO like you did for the Ubuntu ISO, boot from it, and follow the directions to reinstall GRUB.  It should autodetect your setup.
If that fails, you will need to boot from a LiveCD and fix GRUB from there.  If you find that this is the case, I suggest starting a new thread since this is a new problem.  The volunteers in the [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333") part of the forum are good at dealing with GRUB issues, so that might be a good place to ask if using the Super Grub Disk doesn't work.

---

### Post by reinehrdotorg on 2008-12-07
Thanks, Rocket2DMn, I'll try that.

---

### Post by reinehrdotorg on 2008-12-07
Uhm... I'll just add some characteristics of the computer, because i'm afraid that it could have some incompatibilities with the way Ubuntu is normally installed (noticed that after reading this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto))

Intel Core2 Quad Q9550
4x 2.83 GHz 12 MB Cache
64 bits - FSB 1333 MHz
Motherboard INTEL  DP35DPM FSB 1333 MHz DDR2 DUAL-CHANNEL
2 320 GB HD in RAID-0
Memory 4 GB Kingston DDR2 800MHz Dual Channel PC6400

May the RAID-0 could be a problem? Well, i'm downloading SuperGrubDisk and i'll put here the results.

---

### Post by Rocket2DMn on 2008-12-07
Ah yeah, RAID setups can be a pain, historically you've needed the alternate install cd to get it setup (not the LiveCD).  That bit of info may be outdated now, I'm not sure.  If you need help setting up RAID, you're likely gonna have to post outside of this Absolute Beginners forum area.  I'm afraid I don't know anything about actually getting RAID setup, so you might want to check out the Installations & Upgrades area I mentioned before.  Sorry I can't be of more help.

---

