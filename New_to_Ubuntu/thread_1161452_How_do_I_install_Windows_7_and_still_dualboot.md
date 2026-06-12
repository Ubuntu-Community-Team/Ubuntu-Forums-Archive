---
title: "How do I install Windows 7 and still dualboot"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by sunrex on 2009-05-16
Wine is turning out to be a big letdown. Constant crashes. The only good side is Homeworld 2 runs better then in windows. Unfortunently, Homeworld2 refuses to work online in linux. So, back to square one.

How would I go about installing windows 7 and still use linux?. I'm probably going to have to use gparted to shrink the partition down - but after that, I'm assuming ill need to reinstall GRUB.

Anyone know how to do that?.

---

### Post by NESFreak on 2009-05-16
> **sunrex said:**
> Wine is turning out to be a big letdown. Constant crashes. The only good side is Homeworld 2 runs better then in windows. Unfortunently, Homeworld2 refuses to work online in linux. So, back to square one.

How would I go about installing windows 7 and still use linux?. I'm probably going to have to use gparted to shrink the partition down - but after that, I'm assuming ill need to reinstall GRUB.

Anyone know how to do that?.

indeed, make some free space using gparted for windows. After that just install windows to the free space (be sure not to delete the ubuntu partition)

from: [https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB](https://help.ubuntu.com/community/GrubHowto#Backup,%20Repairing%20and%20Reinstalling%20GRUB)
> # Boot your computer up with Ubuntu CD
# Open a terminal window or switch to a tty.
#

Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
# Type "grub"
# Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
# Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
# Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
# Quit grub by typing "quit".
# Reboot and remove the bootable CD.

---

