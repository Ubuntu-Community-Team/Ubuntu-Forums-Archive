---
title: "Old Linux on New Partition"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Transmutable on 2009-09-03
I can't believe no one else has tried this, but I Googled pretty hard. A couple of months ago my Dell Inspirion laptop started going downhill, hardwarewise. After giving it a new hard drive and fighting with Windows XP for three hours I said "screw it" and installed Ubuntu. Everything worked perfectly.

Fastforward to last week. The Dell is continuing to have troubles, primarily with power and battery. It's become more of a portable desktop than a laptop. So it has been replaced with an Asus K50 which so far has just been lovely. Except that it is running Vista, which just sets my teeth on edge. 

I want to dual boot Vista and Ubuntu, and I want the Ubuntu that is on my old hard drive with all my settings and programs and files and so on. I've found tutorials on how to dual boot, and how to back up and restore Ubuntu, but I can't figure out how to connect the two so that I back up my old Ubuntu and restore it to the partition on the new hard drive.

---

### Post by louieb on 2009-09-03
One way to do it:

[LIST]
[*]Using the Vista partition tool or Gparted create **unallocated  **space on the new drive large enough to hold your current Ubuntu partition(s). If you use Gparted be sure the box saying align to cylinder boundary **is not checked**. (Vista is different from earlier MS operating systems).
[*]Get a USB enclosure and put your old drive in it.
[*]Reboot the computer with a live CD containing  Gparted - recommend  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")
[*]Create an **extended partition **using all the unallocated space - know it will seem strange - but the space will still be unallocated.
[*]**Copy and paste** the Ubuntu partitions from the old drive to the **unallocated space** [Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm")
[*]**fix grub** - [Fix Grub after Win install - catlett]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub") - this method will work for you to.
[*]your done - enjoy.
[/LIST]

---

### Post by Transmutable on 2009-09-16
It worked! Eventually, after a bit of finangling. Only now I can't figure out how to boot to Vista. I can see the partition in Nautilus, but when I hit ESC to go into GRUB during boot, all I have is multiple lines of Ubuntu to select.

---

### Post by oldfred on 2009-09-16
You have to add an entry for your windows. Normal installs "see" the windows partition and add an entry like this:

title        Windows Vista  chainloader (on /dev/sda1)
rootnoverify    (hd0,0)
savedefault
chainloader +1

If your system has a hidden partition for creating a new windows disk your entry may be (hd0,1). You can see your partitions by using 

sudo fdisk -l

Note that Grub numbers one less that linux or it starts at 0 where linux starts at 1. so sda1 is hd0,0, sda2 is hd0,1 etc.

The entry should be added to the end of menu.lst

gksudo gedit /boot/grub/menu.lst

---

