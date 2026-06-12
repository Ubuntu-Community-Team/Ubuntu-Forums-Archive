---
title: "Dual boot stopped working"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by mogadon on 2011-03-29
Hi all,
I installed Ubuntu 10.04 onto my Windows XP pc using the windows installer and everything went fine. My only issue was my disk was pretty small and the Ubuntu partition is small, so I have to keep clearing caches....not a big problem. Recently I have purged things pretty well, so I don't think my partition is full.
Last time I restarted the machine the usual dual-boot choice of OS screen came up, but when I select Ubuntu, instead of loading the CD drive (empty) spins a few times and the the computer returns to the BIOS screen and then back to the OS choice. XP loads fine. 
There had been both Ubuntu and Windows updates since I last booted to Ubuntu, but the shutdowns had both been asked for and soft.
Any help would be much appreciated.
Thanks

---

### Post by coffeecat on 2011-03-29
Hi, it sounds as though you have a Wubi install. Also, updates to grub in 10.04 are known to cause problems with wubi installs.

Have a look at the first post in the Wubi megathread:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

From what you describe it sounds as though you have problem #2 for which you'll need the Ubuntu 10.04 live CD.

If you need any help with that, post back here, or add a post to the megathread. If you post in the megathread, please say so here so that people are not helping you in two places.

---

### Post by mogadon on 2011-03-29
Dear coffeecat
I am pretty sure you are 100% correct.
I am working the solution now.
Thanks so much for your help.

---

### Post by garvinrick4 on 2011-03-29
[URL="http://ubuntuguide.org/wiki/Main_Page"]Wrong thread:
[/URL]

---

### Post by mogadon on 2011-03-29
So I think the diagnosis is correct, but I am struggling with the cure.
I downloaded the iso image, ran winMD5sum check on it - it matched the hash correctly. Followed the instruction to burn the CD using InfraRecorder. Put that CD into the machine of interest.
It tries to boot using the CD but it stops at a message: 

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
{initramfs)mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.sqyashfs) on //filesystem.squashfs

I tried to run the Check Disc for defects thing (by holding down a key while booting from the disk you get to a menu where you can choose that option). I got to that menu, chose the check disc, but after a few seconds I get back to an almost identical message (as above). Checking other threads this seems to indicate a corrupt disc, but it's not completely clear.
Any suggestions?
Thanks

---

### Post by coffeecat on 2011-03-30
Yes, I would think this is a bad disc. Your md5sum is OK, but the CD is not behaving properly. A busybox shell is usually because of incompatible hardware (which seems unlikely because you were able to run a wubi Ubuntu) or a corrupt CD.

Two suggestions: burn another CD, but this time choose a low burn speed such as x4 if InfraRecorder will let you. 

Or - does your machine support booting from USB? You can write the ISO to a pendrive such that it becomes a bootable device and you use it very much like a live CD. Here are the instructions for creating one in Windows:

[https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows)

The app usb-creator.exe is in the root of the ISO filesystem. That link tells you how you can extract it.

---

### Post by mogadon on 2011-03-30
You little beauty!

Thanks so much. I burned a new cd (did not have a usb drive big enough for the job), which worked first time. Followed the instructions on the megathread (ran the boot script, figured out which was the win partition, loop mounted the wubi root.disk and edited the grub.cfg file) and everything is fixed - and I feel like a Ubuntu-GOD! (At least here at home, on this message board I know my place ;-)

Thanks a million for taking the time to help.

---

### Post by coffeecat on 2011-03-30
> **mogadon said:**
> You little beauty!

It's been many years since I've been called that! :lol:

I'm glad you're booting problem is fixed. Good luck! :)

---

### Post by kingspider on 2011-03-30
I use ubuntu 10.10 and Windows 7 ultimate 

have had a few problems with dual booting with Grub2 I would recommend using EasyBSD on you windows its makes it a lot easier to dual boot :P

---

