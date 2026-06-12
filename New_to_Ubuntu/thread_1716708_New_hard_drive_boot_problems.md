---
title: "New hard drive boot problems"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by kochinc on 2011-03-28
As a beginner I tried Ubuntu on a 40 G HD with windows XP and it loaded fine and I played for many Hours.  Now I have a brand new 500 G HD I wanted to replace the 40 with no windows at all, it is recognized in CMOS and Ubuntu see's it also, but when I tried to reboot after I ran the CD  load program I get a BOOT Error and the drive goes not further.  I believe I need a Master Boot record to get this thing running but I can't find the correct keystrokes to get it to boot and read the new drive.  I am using Ubuntu 1010 and have a older Dell Dimension 3000 with a gig of ram, could someone walk me thru the initialization and partitioning of the new drive?

---

### Post by mikewhatever on 2011-03-28
By default, the installer puts the Grub bootloader to the MBR. 
Is Ubuntu installed?
Have you changed the default settings anywhere during the installation?

---

### Post by kochinc on 2011-03-28
I loaded and looked at the install, and the MBR was there but I don't know if it wasn't activated or what, I tried again to install with the same results.  I have tried to install 3 different occasions with same results "Boot Error".

---

### Post by Hedgehog1 on 2011-03-28
Please boot off the LiveCD/LiveUSB, select TRY, and then:

Menu to: System >> Administration >> Gparted Patrition Editor

Select the drive that needs an MBR partition table, and then:

Menu to Device >> Create Partition Table

[IMG]http://img834.imageshack.us/img834/8480/gpartedpartitiontable.png[/IMG]

This can also be done from the terminal, using the **parted** command (**man parted** for options)

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-28
If you still have problems after doing gparted/parted, please do this so we can see what is up on the disk and help you:

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by Zanderist on 2011-03-28
Try looking into the Ultimate boot CD,

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

What kind of Hard Drive is this 500 gig? (Connection wise)

---

### Post by oldfred on 2011-03-29
Since your old drive was only 40GB, do you have an older BIOS that will only boot from the first 137GB of a drive. And then how did you partition drive, if you have one very large / (root), you may have boot files beyond the 137GB limit.

I might suggest if that is the case to make a small 20GB / at the beginning of the drive, and then make the rest of the drive /home and 2GB for swap at the end.

---

