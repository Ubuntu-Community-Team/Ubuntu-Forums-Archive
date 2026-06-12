---
title: "Ubuntu from USB loaded to desktop but the Menu Bar is not working"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Ol'Scratch on 2010-10-29
Hi, I'm brand new to Linux in total, so forgive me if it's something simple that I missed.

I downloaded the Ubuntu 10.4.1 desktop for 64bit, and installed it on my Flash Drive (SanDisk Cruzer I believe). I had some initial trouble getting it to even boot the OS, but some googling told me to rename files named isolinux to syslinux, and it boots fine.

The problem is, is that it refuses to run anything, and the menu bar (top bar) is acting strange. The top options of any bar (i.e., for the Applications Bar "Games" and the one above it) cannot be moused over. Once I do, the bars both disappear, and then reset as if I hadn't clicked anything.

Also, anything I try to run says it cannot. I don't remember the exact message, but it was something along the lines of "Cannot start child process." Tried this with both Firefox and the ?-button

Also, for clarity, I'm running ubuntu without installing. I just want to try it out as, again, I'm brand new to Linux.

Thanks for reading

---

### Post by bioterror on 2010-10-29
> **Ol'Scratch said:**
> Hi, I'm brand new to Linux in total, so forgive me if it's something simple that I missed.

I downloaded the Ubuntu 10.4.1 desktop for 64bit, and installed it on my Flash Drive (SanDisk Cruzer I believe). I had some initial trouble getting it to even boot the OS, but some googling told me to rename files named isolinux to syslinux, and it boots fine.

The problem is, is that it refuses to run anything, and the menu bar (top bar) is acting strange. The top options of any bar (i.e., for the Applications Bar "Games" and the one above it) cannot be moused over. Once I do, the bars both disappear, and then reset as if I hadn't clicked anything.

Also, anything I try to run says it cannot. I don't remember the exact message, but it was something along the lines of "Cannot start child process." Tried this with both Firefox and the ?-button

Also, for clarity, I'm running ubuntu without installing. I just want to try it out as, again, I'm brand new to Linux.

Thanks for reading

Sounds kinda weird.
You've made your LiveCD with old school technics.

I suggest you to try out Unetbootin ([http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")). It's the easiest way to put ISO to a USB stick with Fat32 Filesystem.

And you should also confirm the md5checksum of the ISO file, that it's not corrupted or something.

---

