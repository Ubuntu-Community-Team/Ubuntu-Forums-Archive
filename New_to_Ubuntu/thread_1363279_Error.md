---
title: "Error?"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by ken0069 on 2009-12-24
X86 ubunbu 9.10  Got another crash this morning with the following message.  Oh, this is the second time this has happened in a week.

Failed to execute child process "oofice" (No such file or folder)

Had to do a hard reset to get it back as even though the mouse worked, no icons were on the desktop and it refused to shut down.

---

### Post by Akavashi on 2009-12-24
More details please, like what have you removed/installed right before the problem started?

---

### Post by ikt on 2009-12-24
> **Akavashi said:**
> More details please, like what have you removed/installed right before the problem started?

Also a good chance to take a look at the system logs.

System > Administration > Log File Viewer, check for error messages near to 

"Failed to execute child process "oofice" (No such file or folder)"

---

### Post by 3rdalbum on 2009-12-24
oofice isn't the correct name. It's ooffice. But I realise that this isn't the problem you are asking about.

Usually if everythinhg freezes up, you can kill the X server by pressing Alt-SysRq-K (SysRq is the same as Print Screen). This dumps you back at the login screen.

---

### Post by ken0069 on 2009-12-25
A little background.  I've got a network configured thru a Cradlepoint Router with 4 computers and a wireless HP InkJet print, scan and fax.  Three of these computers are "multi-boot" systems with 2 or 3 operating systems on them with each OS installed on it's own hard drive.  NO GRUB CONTROL OF BOOTING.  I choose what OS/HD I want to boot from in BIOS.

I had problems trying to install SAMBA last week because I couldn't share files on these ubuntu installs with other computers on my Windows network.  If memory serves, I finally did get SAMBA to install on here after getting errors on some package updates.

Didn't find anything in System Logs that resembled the error message I got on the crashes.  I did find this though that seems to be related to an HP wireless printer we have here on the network.

Dec 25 21:51:53 ubuntuYELLOW udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb8
Dec 25 21:51:53 ubuntuYELLOW udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 25 21:51:53 ubuntuYELLOW udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 25 21:51:53 ubuntuYELLOW udev-configure-printer: Failed to get parent

Both times the crashes have occurred has been when I had several apps open at the same time so I got no idea if or which one of those could be the problem.  The computer in question has both Windows XP and Windows 7 installed on their own drive.

If this keeps happening and we can't figure it out, I may just go ahead and do another clean install since I've gotten pretty good at that lately!

Thanks,

Ken

---

