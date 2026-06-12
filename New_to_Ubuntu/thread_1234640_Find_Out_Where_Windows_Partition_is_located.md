---
title: "Find Out Where Windows Partition is located?"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by justinram22 on 2009-08-08
Hello,  I dual boot ubuntu 8.10 and Windows XP Pro (for gaming).  Recently windows got a nasty virus (gotta love windows *wink*) and i was forced to reinstall.  Now window's boot loader has overwritten grub boot loader.  I'm following this tutorial

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

And am good until this part...

> 
Note that you should also verify that hd0,0 is the correct location for Windows. If you had installed Windows on the 4th partition on the drive, then you should change it to (hd0,3)


I'm confused as to how to find what partition windows is located on.

Is there a terminal command that can tell me? Thanks to anyone who can help!!

---

### Post by Cato2 on 2009-08-08
try this:

sfdisk -uM -l | less

Look for filesystems near the front of the disk that are labelled HPFS/NTFS or W95 FAT32.  The MiB column gives the size in megabytes, check this is what you expect.

To be really sure, try mounting the filesystem in question from Ubuntu.

Once you have a device name such as /dev/sda1, you need to translate this to Grub's scheme.  You subtract one from the number, and usually map 'sda' into 'hd0', so this example would be (hd0, 0).

Read a GRUB howto on how to check that this device name is correct - see [https://help.ubuntu.com/community/GrubHowto#Changing%20the%20Disk%20that%20Grub%20is%20installed%20to](https://help.ubuntu.com/community/GrubHowto#Changing%20the%20Disk%20that%20Grub%20is%20installed%20to) in particular.

If all this is too complex, just burn a copy of SuperGrubDisk to a CD, and boot it.  Makes it quite simple to sort things out.

---

