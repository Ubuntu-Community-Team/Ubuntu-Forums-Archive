---
title: "Installing Windows 98 after Ubuntu"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by E-1000 on 2010-05-22
Hi, first of all, I have searched, and I have found 1 thread talking about this, but I don't get get anything of it. By the way, the thread is: [http://ubuntuforums.org/archive/index.php/t-310403.html](http://ubuntuforums.org/archive/index.php/t-310403.html)

I have Ubuntu 10.04, and Windows XP installed on my computer. I need to install Windows 98. I have created a FAT32 partition, but when I use the Windows 98 boot CD (not a floppy disk), and run the setup.exe, it show me an error saying that it cannot be installed on a NTFS/HPFS partition. "Error Message: "Cannot Create a Temporary Partition. If You Have HPFS or NTFS Installed on Your Hard Drive" When You Install Windows on a Guest PC".

What should I do?

---

### Post by Kellemora on 2010-05-22
Hi E

No can do without also having to redo your boot sector too!......

The NTFS it's referring to is probably what it sees in the MBR........

I forget now which it is Partition Magic are Gparted that lets you HIDE the disk partitions so Windows can't see them.
Then you can install Win95 or Win98, but after you do, THEN you will have to reload GRUB to get everything back up and running again.
And if you use any of the disk tools in Win95 or Win98, they will wipe out your boot sector every time.

You could install Grub on another partition out of Windows way.
Or pick up a cheap small 2nd hardrive just for Win95 or Win98.

Good Luck!

TTUL
Gary

---

### Post by snowpine on 2010-05-22
The elegant solution is to run Windows 98 as a "guest" operating system within a Linux "host" by using VirtualBox or a similar solution: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

This would allow you to run your Windows application without the massive security risks of running a 12-year-old, unsupported Windows release as your main operating system. :)

---

### Post by cariboo on 2010-05-23
+1 for running Win98 in vbox, I've done it, it worked great.

---

### Post by lkraemer on 2010-05-23
While I wouldn't recommend installing Win 98 or Win 98SE as Dual Boot
with Ubuntu, there is a nice article on Installing XP after Linux.
I'm sure you could follow the same method for Win 98xx.
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

If you do use Win98 in Virtual box, be sure to install the vesa drivers from:     [http://www.bearwindows.boot-land.net/vbe9x.htm](http://www.bearwindows.boot-land.net/vbe9x.htm)
as shown at:
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

lk

---

### Post by sylvester_0 on 2010-05-23
I'll echo everyone's suggestion to use a virtual machine (do you really need it on the hardware?), but the error message that you're receiving is Windows simply complaining about not having a filesystem to copy temporary files to during setup. Simply create the FAT32 partition from within Linux and try running setup again. Also, are you sure that your disk controller/hard drive (it may be too large) will be recognized by Win98?

---

### Post by oldfred on 2010-05-23
If the boot flag is still on the NTFS partition that may be why it is complaining. and it has to be a primary partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by new_tolinux on 2010-05-23
I would suggest at first (like the others) to use a virtual machine instead of installing another operating system on your computer.
XP and on are mostly using NTFS -> Win98 can't read that (XP can read FAT and FAT32, so no problem from there).

Windows 98 probably won't run nice on your computer anyway, because there are no drivers.

If there's really no other way, I'd suggest a very tricky way which is using a partition manager to create space _before_ the first partition. Win98 doesn't really like being on another than the first partition. You'll have to format it in FAT/FAT32, Windows 98 won't do that for you (it can, but afaik only on an unused disk which is at that moment the only disk in your system).
Even then it's preferable to get your hands on an old computer which is known to run 98 well, because, as said, your current hardware will probably not be supported by windows 98 so you'll end up with at most an 800x600 screen resolution, no network, no sound, etc.

---

