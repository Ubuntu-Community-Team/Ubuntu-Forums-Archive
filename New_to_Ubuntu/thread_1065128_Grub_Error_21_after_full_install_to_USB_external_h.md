---
title: "Grub Error 21 after full install to USB external hdd"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by ManoC on 2009-02-09
I have windows xp in my computer and i installed linux ubuntu in my usb external hdd.I can boot linux or windows normally .But the problem is that when i am trying to start my computer without the usb (of externall hdd) connected, i get this message:
Grub 1.5 Error 21 .How can i fix this ? Thanks in advance. Sorry for my bad english. :) ):P

---

### Post by logos34 on 2009-02-09
You need to reinstall Grub boot loader onto the USB drive MBR. (see link in my signature).  

~ like this:

**sudo grub**

> **root (hd1,x)**
> **setup (hd1)** --> this writes grub to the USB MBR, as opposed to '(hd0)' which would put it on the internal disk

If you're using 8.10 you don't need to worry about editing 'root' lines stuff in menu.lst (it uses UUIDs exclusively). Change the Bios hard disk boot priority so the USB is first.

Restore windows boot loader to the internal drive, either using the XP install cd (>'R' for 'Recovery console'>'fixboot' at prompt) or Super Grub Disk (see link in my signature).

Either that or just reinstall ubuntu [like this]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/").

---

