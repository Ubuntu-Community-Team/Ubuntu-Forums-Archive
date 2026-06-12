---
title: "Uninstalling GRUB2"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by garl on 2011-04-30
Right now I have two hard drives, one with Windows 7 and one with Ubuntu. I had been using a different hard drive with Windows XP, which was dual booting with the Ubuntu drive before I reformatted it. I just want to hook up my old Windows XP hard drive by itself to access some files, but it gives me some error message about GRUB and doesn't boot. How can I remove GRUB from the old hard drive to boot Windows XP? Tyia.

---

### Post by oldfred on 2011-04-30
If the old XP disk was a dual boot, it has an old grub.

You can use an XP disk and run fixMBR to write a new MBR.

Or you can install from Ubuntu the lilo MBR boot loader (not all of lilo). Lilo works just like windows in that it looks for a boot partition and jumps to that partition to continue to load. If windows has its code in the partition then windows will boot. Check which drive it is, example is for sda, but it may be sdb, sdc etc.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

FIXMBR  C:  #do not run if you still want grub in the MBR

Other commands if windows still needs fixes:
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

