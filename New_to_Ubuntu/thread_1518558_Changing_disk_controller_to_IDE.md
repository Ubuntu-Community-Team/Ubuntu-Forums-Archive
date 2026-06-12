---
title: "Changing disk controller to IDE"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2010-06-26
My friend was trying to reinstall XP so he could dual boot. However, when he tries, it says that it can't find any hard drives for windows to install on. This seems to be because the device controller needs to be in IDE mode. Unfortunately, there doesn't seem to be an option in his current BIOS version to change the device controller. 

A newer BIOS version has the ability to do so but funnily enough, it uses WinPhlash to flash the bios, which is run in the windows environment. So, to install windows, he needs to flash his BIOS but to flash his BIOS, he needs windows installed :(.

I've tried the section at the bottom of this wiki: [https://wiki.edubuntu.org/DellBIOS](https://wiki.edubuntu.org/DellBIOS) but when running Winphlash with wine, it doesn't create the BIOS.ROM file as suggested.

Is there any way around this pickle of a problem?

---

### Post by Zeike on 2010-06-26
You could use a newer version of windows.

XP is nine years old now.

EDIT: you might be able to use windows XP if the disc you have includes SP1

---

### Post by jerome1232 on 2010-06-26
A very roundabout way would be to install windows in a virtual machine (or use another machine running windows) and use nlight to slipstream the drivers and make a new recordable bootalbe cd-r that you can install from (the drivers will be included because you added them)

google nlight tutorials and you should be able to figure it out.

---

### Post by lkraemer on 2010-06-27
Your posting is slightly in error.  The problem you are seeing is due to
Windows XP not having the SATA Drivers installed, not in changing the
controller to IDE.  No hardware needs to be changed/replaced.  XP only
has the IDE Drivers included on the CDR.  You can locate the drivers,
put them on Floppy, and boot the Windows CDR, and then choose to copy
those from Floppy with a function key.  If memory serves me right, it
is F6.  Or, as suggested in the previous post, you can Slipstream the
latest Service Pack (SP) into XP along with the Correct SATA Drivers,
and also make a Tiny Version, by running Nlite on your Windows CDR.
So, Google: Slipstream XP, Nlite, etc.

There is another package that allows you to do just about the same as
Nlite, but right now I forget it's name.  Google should be able
to locate it when you search for "HOW to Slipstream XP".

If you really want to Flash the BIOS, most BIOS manufacturers have an
easy way to make a Flash Boot Disk that will do the job for you.  Find
out what BIOS you have, go to their site and search for "How to Flash
BIOS".  Google should also find the same........  

WARNING: Doing the FLASH improperly WILL KILL your Computer, so make 
double sure you know what you are doing, and hope power doesn't go off
during the process.

Also, read up on installing XP after Ubuntu is installed, because Windows
wants to be the ONLY OS installed and doesn't play well if Ubuntu is
already installed on the Hard Drive.  There are guides for making it
work.  APC Mag has a couple good articles.

lk

---

