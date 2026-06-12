---
title: "Bad Image error after uninstalling"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Nick11202 on 2009-12-20
After uninstalling Kubuntu 9.10, I am getting bad image errors for a few of my programs, and the computer is generally running slow. I "uninstalled" kubuntu by deleting the partition, and then using a program called mbrFix, which deleted GRUB. I have no recovery disks for this computer. Does anyone know what I did wrong, or does this have nothing to do with Kubuntu?

---

### Post by diablo75 on 2009-12-21
I'm going to out on a limb and try to guess at a few missing details you haven't mentioned explicitly, but I think are true:

-  You were dual-booting Windows with Kubuntu
-  Kubuntu was installed on its own partitions with a swap partition as well (you selected Guided Resize during install and it did the rest for you).
-  These error messages you are getting are coming from Windows, and not a Linux based OS.

Is this correct?

If so, what program are you trying to run in Windows that is producing this error?  Did you resize your NTFS partition back out to fill in the unallocated gap created when you deleted the linux ext3/4 and swap partitions?  Have you tried running the Scan Disk utility included with Windows to check for file allocation table errors (Right-click on a hard drive>Properties>Tools tab>Error Checking/Check Now button (reboot will be required).

---

### Post by Nick11202 on 2009-12-21
Thanks, I would try this, but... I can no longer log in to kubuntu, and GRUB has magically disapeared. When I try to log into Kubuntu, it flashes to my desktop, with a console window open, and then flashes back to the login screen, although, I can log in fine with terminal log in. Also, I can no longer boot into windows, and have no way of using my other computer.
EDIT: By other computer, I mean the one with Kubuntu installed.

---

