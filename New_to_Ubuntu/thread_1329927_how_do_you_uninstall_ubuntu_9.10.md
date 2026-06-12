---
title: "how do you uninstall ubuntu 9.10?"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by ireallydontcare on 2009-11-17
Hi,

i've installed ubuntu 9.10 on my acer aspire one xp (dual boot) and now want to uninstall it. i know you can do it with a windows live cd but the aspire one doesnt have a cd drive.

someone please helppp

---

### Post by RandomP on 2009-11-17
How did you install it?

---

### Post by NickJones on 2009-11-17
UnetBootin should help.

---

### Post by NickJones on 2009-11-17
Then use this to get rid of GRUB
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by NickJones on 2009-11-17
And then finally use some form of Partition Manager from within Windows to re-format the EXT4 partition into Fat32 or NTFS.

---

### Post by ireallydontcare on 2009-11-18
i used the unetbootin to make a usb bootable and then installed it from that when it started up. yeh i have been trying to fix the mbr but cant because i cant get to the recovery console because of the GRUB loader

---

