---
title: "Windows 7 overwriting Grub! Help!"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by Tubbytee on 2009-10-27
Ok - I'm a little stuck!

I had Windows XP and Ubuntu 9.10 running really happily in a dual boot situation, using Grub to select which one I wanted to boot into.
I installed XP first and then Ubuntu and all the setting up of Grub was done by the install of Ubuntu

However, I got a copy of Windows 7 to try and installed it over the XP partition of the drive, thinking that Grub would still come up offering the choice of OS to boot into! WRONG!

It seems that even though I didn't let win7 format or change any drives, it has altered the MBR so now I can only boot into Windows! Do I need to re-install Ubuntu now, or is there a way I can reset things so that Grub gives me the options again?

Thanks in advance for your help, I'm new to Ubuntu, but love it, I just need to use windows for my work (boo!)

Pierce

---

### Post by danielkabrinski on 2009-10-27
Looks like you have to reinstall Grub (step 4):
[URL="http://http://ubuntuforums.org/showthread.php?t=1035999"]
http://ubuntuforums.org/showthread.php?t=1035999[/URL]

If that wont work, you may have to use 7 as your primary OS and edit its boot.ini (if you can, not that familiar with 7/Vista 2.0)

EDIT:

Why do you need 7 for work?  I think you can run Office 2007 in wine...

---

### Post by blazemore on 2009-10-27
Here's a good guide to getting Grub up and running. If it doesn't work with the Karmic LiveCD, see if you can find an earlier one.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by northd_tech on 2009-10-27
Booting off your ubuntu CD/DVD should work (then running 'sudo grub' as Blazemore recommends above).

Alternately, you can use Trinity Rescue CD:

[http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

Or Super Grub Disk (on CD, USB, or hard disk):

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I would be sure to read the documentation thoroughly either way **first**.  It looked to me like Super Grub Disk was not originally written in English, and I found it somewhat confusing (but was able to recover Grub using it).

Once your Grub bootloader is back from the dead, your earlier Linux install will likely be very close to normal (depending upon how everything was partitioned).

---

### Post by Tubbytee on 2009-10-27
Guys, first of all a big thanks for the speediness of your replies!:KS

Blazemore, your link worked perfectly, it's all up and running now just how I want it!

Thanks again guys, I think this community is what makes Ubuntu and Linux fantastic!

Pierce

ps Daniel, it's Sibelius that I need windows for (and a little online poker!;))

---

