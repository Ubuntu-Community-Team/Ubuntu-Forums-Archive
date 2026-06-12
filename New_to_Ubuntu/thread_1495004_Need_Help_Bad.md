---
title: "Need Help Bad"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by arayray94 on 2010-05-27
ok i dual booted ubuntu 9.04 and windows 7 so i tryed to format the partition of linux to reinstall due to internet drivers not working and when i rebooted i got a screen with this
 
 
error: no such partition
 
so i went into bios tryed to make it so my pc would boot stragiht from my usb (because i have a netbook and no cd/dvd drive) and it wont work
 
can someone please help and is all my files on windows 7 lost :mad:

---

### Post by Zemblan on 2010-05-27
If you deleted the ubuntu partition then you also deleted the files that grub (the bootloader) needs to boot. So it looks for them and cannot find the partition they are supposed to be on. Unless you deleted your windows partition too windows is probably fine, along with all your files. Just that grub wont work any more, so unless you can fix it, or install the window bootloader from a windows recovery disk, you wont be able to boot windows.
Easiest way is to install ubuntu or some other distro to a usb drive, and boot from that. Not sure what specific problems you are having with that process so I can't offer any useful advice for that.

---

### Post by -humanaut- on 2010-05-27
See if you can get an External drive for running a LiveCD sounds like you'll need to reinstall Grub but your netbook should be able to boot off a USB key if the system is installed correctly If you know anyone else running Ubuntu you should try a new image with the USB Creator tool. If you deleted the Ubuntu partition everything Ubuntu is gone, if you Deleted the Windows partition everything is gone. Does your system offer a restore option?

---

