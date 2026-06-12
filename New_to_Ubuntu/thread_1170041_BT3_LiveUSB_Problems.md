---
title: "BT3 LiveUSB Problems"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Alex12us on 2009-05-25
I have been trying to get the live USB of BT3 to boot for quite a few hours (Asus Eeepc 1000HE), and I had no luck.  I searched online for solutions, but could not find any.  I have a dual boot Windows XP and Ubuntu 9.04.  I usually switch in the GRUB menu when dual booting.  Now, I have already set the Netbook to boot from the USB first before booting from the harddrive, but BT3 still doesn't show up.  Is there a way to edit the GRUB menu to force the boot from the USB? Is there a way to move BT3 into my Ubuntu root folder and have the GRUB menu boot from that very folder without creating another partition? Any help would be greatly appreciated.

---

### Post by profeta81 on 2009-05-25
if the grub menu shows up, it means that the BIOS has not detected anything bootable on the USB... how did you create the live distro on the flash drive? did you partition the drive yourself (with ext3 or ext2)? did you simply copy the files once the iso file and the drive where mounted by linux?

try this (maybe it'll be enough to make the flash drive bootable): unmount the drive if it is, open gparted, select the partition on which you installed the bt3 files and make that partition bootable (partition -> manage flags and then tick the flag boot).

sorry, never used bt3 (i guess you mean BackTrack 3) so maybe I won't be of much help...

---

