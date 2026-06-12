---
title: "external drive, insatallation issue"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by protpisys on 2010-08-22
I have a Toshiba Satellite laptop with a My Book Essential 640 GB external drive that I leave attached pretty much all the time. The problem is that I had it attached when I installed Ubuntu and now my computer won't boot unless it's hooked up. I get a grub error message and prompt and the thing is as good as dead. I plug the usb back in and it's good to go. The other problem is that the install took over half the external drive, I have burned the gparted live disk, but before I deal with that I would like to get the 8.71 GBs on the external drive moved into the computer's hard drive, the C drive in ms. So, is there a way to do this, or should I just reinstall with the external drive unmounted? I'd rather not as I've been tweaking and installing for a couple of days now and wouldn't want to have to start all over again, but can if necessary to make my laptop portable again.

---

### Post by john newbuntu on 2010-08-22
It appears like the first part of GRUB2 bootloader has been installed on your first disk and the main parts including the Ubuntu install are in the external drive, which is why your boot fails. I am assuming you have windows in the internal drive. Just FYI, Gparted should already be on your external CD and you need not have to burn one.

You could use clonezilla by installing it from a liveCD boot to backup your ubuntu partitions.

Here are a few options you have(among others):
1. Use windows to boot Ubuntu/Win from disk1.  Use GRUB2 (Ubuntu) to boot Ubuntu/Win from disk2 (if present) depending on the drive chosen by BIOS as boot drive.   This will involve restoring the Win MBR and re-installing the grub2 to /dev/sda2 (external drive). Finally, use gparted and just resize the space used by Ubuntu in the external.

2. Create a partition on your internal drive by clearing some space in Win(approximately 15GB), partitioning it appropriately and copy/clone existing ubuntu.  Re-install grub2 to MBR.  Now your external disk is free.

3. Reinstall ubuntu in the internal drive after clearing some space as you mentioned. Once again your external disk is free.

Which option would you prefer?  What version of Win do you have? In any case, please follow the instructions on this page  [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) to download and run the boot_info_script and post the output using code tags.  Someone here will help you.

---

