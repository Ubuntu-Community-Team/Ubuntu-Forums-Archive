---
title: "Grub - no such disk"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by rennie21 on 2009-12-30
ok, so despite 2 years of linux I know next to nothing about how to troubleshoot problems... I went back to windows about a year and a half ago. I kept one of my old hard drives with ubuntu on it, but never actually used it for anything but transferring old files off of. I always intended to get the OS going again for blender rendering (dual booting was the goal). Well, I tried and failed miserably.

**Hard drives/OS, before:**

400 gb hard drive partitioned... (this is the primary hard drive)
100 gb partition ntfs (WINDOWS)
300 gb partition ntfs (no OS)

40 gb hard drive ext (Ubuntu 8)

40 gb hard drive FAT (no OS)

I downloaded the current version of Ubuntu, 64bit yesterday (I have a core 2 quad). I ran the install and chose to overwrite the 40 gb hard drive that already had ubuntu installed on it. FYI, the boot loader from when I was using this hard drive, I assume was inactive or on one of my old disks, as it wasn't popping up when I started my computer. I used all of the default options when installing. Later I realize this chose (hd0) as the location for the boot loader, I assume grub2.

**So after install the hard drives/OS should have been:**

sda
400 gb hard drive partitioned... (this is the primary hard drive)
100 gb partition ntfs (WINDOWS)
300 gb partition ntfs (no OS)

sdb
40 gb hard drive ext (Ubuntu 9)

sdc
40 gb hard drive FAT (no OS)

**Upon restart, I got the error:**

GRUB loading.
error: no such disk
grub rescue>

I searched the forums to come up with a solution, but didn't really find anything I understood or that worked. I tried reinstalling choosing both sda and sdb as the location for the boot loader. Niether of these worked either.

**The existing setup of hard drives/OS is:**

sda
400 gb hard drive partitioned... (this is the primary hard drive)
100 gb partition ntfs (WINDOWS)
300 gb partition ntfs (no OS)

sdb
40 gb hard drive ext (Ubuntu 9)

sdc
40 gb hard drive FAT (no OS)

The last place I tried to install the boot loader was on sda.


typing "ls" after the "grub rescue>", i get:

(hd0), (hd0,2), (hd0,1)

trying to do "set root=(...)" for all the combinations I can think of: I either get "no such disk", "no such partition", or "unknown filesystem"


Also of note, when I go to the bios/startup boot menu, the only options are my 400gb hard drive or my cd drive. The other drives don't appear. Could it be something in my bios or the way I installed my hard drives? They mount ok from the livecd, so I assume not...


Any ideas what I should do?
Do I need to remove all of the grubs I've installed all over the place? I assume I put it in the wrong place initially, then in the right place, but the wrong place grub needs to be deleted, but then again, I'm a complete linux idiot...

Please help!! I can't start windows or ubuntu anymore, my computer is a footstool right now.

Thanks!

---

### Post by LuisGMarine on 2009-12-30
I had somewhat of a similar problem.  When i edited the "root" line in grub I changed mine from (hd1,0) to (hd0,0)  try changing that field and see if it works ...  Just thought I throw in my 2 cents.

---

### Post by oldfred on 2009-12-30
Lets see your entire configuration. I always prefer to have grub in the same MBR as the install of Ubuntu.

Boot Info Script 0.42 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by rennie21 on 2009-12-31
SOLVED

unfortunately, this was anticlimactic... I appreciate the vigor with which the community began to attack this problem, but:

The actual problem had nothing to do with Grub2, Grub legacy, ubuntu or my old and new installs.

My BIOS wasn't set to identify my other 2 hard drives. Once I set this Grub started right up.

LiveCD back on the shelf.

Thanks again for trying to help!

---

### Post by LuisGMarine on 2009-12-31
Sweet enjoy Ubuntu then =)

---

### Post by theozzlives on 2009-12-31
If your BIOS isn't detecting the HDDs, you can't expect GRUB to. Check your cables, jumpers, etc. and get the drives in the BIOS.

---

