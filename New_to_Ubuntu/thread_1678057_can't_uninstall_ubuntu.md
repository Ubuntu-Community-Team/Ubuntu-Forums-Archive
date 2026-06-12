---
title: "can't uninstall ubuntu"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by psanscarti01 on 2011-01-29
I tried removing 'Ubuntu' with the 'Add/Remove' app in Windows XP, but I get an error message stating that I don't have access to 'uninstall-wubi.exe'.  That's contrary to what the Ubuntu install disk message read; that Ubuntu can be removed as any Windows software by this method. 

I originally loaded Ubuntu to a flash drive, not my hard drive, and suspect this is the problem.  I want to remove Ubuntu (and install it to one of my 2 hard drives).

I think Ubuntu runs slower from a flash drive.  I tried removing the flash drive and rebooting, but there's this 'GRUB' command on a black screen.

Any ideas, remember, I don't know much about computers, enough to screw things up.
Thanks

---

### Post by waynefoutz on 2011-01-29
boot off your Windows XP install disk, follow the prompts to get to the "recovery console" which is nothing more than a dos prompt. the type "fixmbr" without the quotes. It will boot right into Windows after that.

---

### Post by dirghrabadia on 2011-01-29
Running from a LIVE CD/DVD/USB tends to make Ubuntu slower. 
Did you install Ubuntu on a separate partition from Windows?

If you want to install it along with XP, following these steps might help:
1. Make a LIVE CD/DVD of GParted, run it, and shrink the Windows volume enough to install Ubuntu.
2. Convert the partition for Ubuntu to ext3 filesystem.
3. Download the image file for Ubuntu, check for its integrity using md5sum, burn it on a CD/DVD.
4. Run the Ubuntu LIVE CD/DVD, and choose the manual partition option (as Ubuntu 10.10 is known to have wiped out Windows for a few users before, if you choose the Automatic side-by-side installation). 

Rest of the steps should be easy to follow. Good luck & I hope you enjoy the ride :)

---

### Post by psanscarti01 on 2011-01-29
Ah... don't have he Windows XP install disk, bought the computer used.

Kinda lost by the instructions of the second reply, but I'll work on it.

Thanks to both for your help

---

### Post by wilee-nilee on 2011-01-29
You can install a linux bootloader called lilo, from a live Ubuntu cd booted; to restore the MS boot.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

These commands would be if your HD is sda, if the HD is another adjust accordingly. You sound as though you can't boot XP on its own, this will reload a bootloader that will.

You can also transfer the wubi to a partition.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Tengen Toppa tux on 2011-01-29
It should be on a separate partitian? in this case you can wipe the partitian on the drive and then go about your business, also you could tourant the windows xp iso then hopefully your computer has the registration code on it

---

