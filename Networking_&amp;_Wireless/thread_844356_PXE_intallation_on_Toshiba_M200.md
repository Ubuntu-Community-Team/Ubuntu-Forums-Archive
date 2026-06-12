---
title: "PXE intallation on Toshiba M200"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by theragingking on 2008-06-29
(Originally posted to "Absolute Beginner")

Hey all!

I'm looking to do a PXE boot of Windows XP 2005 Tablet Edition SP2 (not mine, my friend's ::rolls eyes:: ) on a Toshiba Portege M200. THis will be a clean installation, not from the backup CD/DVD. I have the disks for the OS, but no external CD rom for the tablet. I also have no Idea how to set up a PXE server in Ubuntu (Gutsy Gibbon), or how to install an OS over the network. I know how to get the Tablet to look for the server, but that's about it.

Any help?

---

### Post by dmizer on 2008-06-30
instead of setting up a pxe server, you might find it infinitely easier to install from a usb key instead.

here's the howto on installing from a usb key:
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

here's the howto on pxe boot install:
[https://help.ubuntu.com/community/PXEInstallServer?](https://help.ubuntu.com/community/PXEInstallServer?)

when i did a pxe install, it was excruciatingly difficult and i really had to fiddle to get things to work.  i did use the pxe howto i linked above, but that howto was written back in dapper, and there have not been many updates to it recently.

the usb key was way easier, and worked the first time.

---

### Post by theragingking on 2008-06-30
Thank you very much for the links!

The only problem is that I don't need to install linux on this thing, but Windows XP Tablet Edition 2005. I find plenty of tutorials for doing this *from* a windows machine, but I'm working from an Ubuntu machine.

See why this started in asolute beginner? ^.^'

---

