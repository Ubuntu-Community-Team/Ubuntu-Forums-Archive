---
title: "Installing Ubuntu 10.10 over Ubuntu 9.10, when windows 7 is side by side."
date: 2011-07-10
forum: New to Ubuntu
---

### Post by sstextile on 2011-07-10
I have downloaded Ubuntu 10.10 through uTorrent. I got it burned to DVD. When i started Ubuntu 9.10 and inserted the DVD containing ubuntu , its not installing it.
Please help me replacing Ubuntu 9.10 by Ubuntu 10.10. It should not disturb windows 7 (which is installed side by side to Ubuntu 9.10)

Also tell me how i can do it by pen drive.

---

### Post by Psyco430404 on 2011-07-10
When you boot from your 10.10 disk, just select the ubuntu 9.10 partition and it will write over your current ubuntu install.

MAKE SURE YOU BACK UP YOUR FILES!!!

as far as the pen drive booting is concerned, just use unetbootin and it does everything for you. Just select your iso and pen drive.

---

### Post by peter d on 2011-07-10
Make sure that you burn the ISO as a disk image, not as just a copy.

Back up any data you can't afford to lose. You shouldn't lose any but better safe than sorry.

Put the DVD in the drive and restart the machine. Make sure that your PC boots first from the DVD drive.

Install 10.10 on the partition currently occupied by 9.10.

Windows 7 should be untouched.

---

### Post by rosencrantz on 2011-07-10
To do it by pendrive, download unetbootin (for Windows)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
or usb-creator (Linux), create the pendrive and set it as the first boot device in the BIOS.
Make sure you do a full backup of /home
If you want to restore all packages in your old install, try

dpkg --get-selections > file
cat file > dpkg --set-selections
sudo apt-get dselect-upgrade

as described in this thread:
[http://ubuntuforums.org/showthread.php?t=169062](http://ubuntuforums.org/showthread.php?t=169062)

---

### Post by critin on 2011-07-10
> i started Ubuntu 9.10 and inserted the DVD containing ubuntu , its not installing it.

If this is a live cd you start the computer with it in the drive, without starting the 9.10.  The computer must boot from it or from the usb (whichever you use).  Watch the screen when you turn it on and note the key for 'BOOT' which is usually in a right  corner, either at the bottom or top right.  Click that key and choose to boot from cd or usb, then let it boot.

critin

---

