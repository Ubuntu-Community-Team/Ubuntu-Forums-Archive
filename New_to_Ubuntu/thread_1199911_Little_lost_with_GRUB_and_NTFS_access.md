---
title: "Little lost with GRUB and NTFS access"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Anospa on 2009-06-29
I have XP and Windows 7 RC installed on the first two partitions of my RAID 0 array, and have Ubuntu 9.04 installed on the 3rd partition, and the rest set to another NTFS partition I was going to use to share documents between all 3 OSes.

I installed Ubuntu off of the alternative CD, so that the RAID array would be detected, and the install worked flawlessly.

Windows XP and 7 can access each other's partitions and the shared partition.  Ubuntu cannot see either, nor can it see the shared partition.  

Ubuntu can access my 3rd HD, which is formatted with NTFS, so I'm not sure why it can't see the rest of the RAID 0 array.


Also, I'm having some problems with GRUB.  I can boot into Ubuntu straight from GRUB no problem, but when I try to boot the Windows bootloader (says Vista loader), I get an error "21: Selected disk does not exist."  I know that the windows installations are still intact and usable, as I've used the super grub boot disk to boot into them using the Windows, boot Windows tool.

I tried rebuilding GRUB before, but I didn't really know what I was doing, and ended up ruining my windows installation, so I'd like to avoid doing that again...

---

### Post by Zimmer on 2009-07-03
No experience with RAID but to overcome problems dual booting with VISTA I chose to install GRUB to the Ubuntu partition and NOT the MBR.

I then installed EasyBCD to VISTA and use that to control booting.

You may need to recover your MBR on the boot partition (either the XP or W7) and go from there.
These links may provide you with further info.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

[http://www.multibooters.co.uk/](http://www.multibooters.co.uk/)

---

### Post by ronparent on 2009-07-05
Ubuntu may not be automatically mounting the ntfs partitions. Since your raid partitions are apparently active, you should find all of your partitions referenced in /dev/mapper (ie ls /dev/mapper). Each of the files listed in that directory are actually the mountable symbolic links representing your partitions. You should be able to add them to the /etc/fstab to automatically mount any of them on boot. Be aware that if these symbolic links exist, you will have to manually create the locations in your filesystem to mount them to. 

I don't know the level of your linux experience so I've only sketched the general process for accessing the ntfs partitions here. If you need more specific instructions, post your inqueries here.

---

