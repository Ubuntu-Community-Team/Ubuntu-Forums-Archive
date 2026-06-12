---
title: "NVIDIA graphics card incompatible?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by undying23 on 2009-04-15
Hello,
every time i attempt to enable my nvidia graphics card (version 180) with Ubuntu 8.10, after restarting my computer, i receive a message saying "Ubuntu is running on low graphics mode". I'm a n00b to Ubuntu and i would like to know why my graphics card isn't working so that i can enable desktop effects, play games etcetera. If you need any additional information, feel free to ask
here's what it told me:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux Gregory 2.6.27-14-generic #1 SMP Fri Mar 13 18:00:20 UTC 2009 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 15 02:23:36 2009
(==) Using config file: "/etc/X11/xorg.conf"
NVIDIA: could not open the device file /dev/nvidia0 (Input/output error).
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:0:13:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by Kosimo on 2009-04-15
Do you know the specific model of your nVidia card?

---

### Post by undying23 on 2009-04-15
> **Kosimo said:**
> Do you know the specific model of your nVidia card?

Here's my computer's info, also, just in case..
AMD Athlon 64 X2 5200+ 
2.6GHz -2GB DDR2 SDRAM 
500GB SATA hard drive
NVIDIA GeForce Go 6150

i'm dual-booting with vista because vista is terrible.

---

### Post by Kosimo on 2009-04-15
> **undying23 said:**
> Here's my computer's info, also, just in case..
AMD Athlon 64 X2 5200+ 
2.6GHz -2GB DDR2 SDRAM 
500GB SATA hard drive
NVIDIA GeForce Go 6150

i'm dual-booting with vista because vista is terrible.

Should be supported by the 180.xx or 185.xx Drivers.
You can give a try to a manual installation if you want.

Just disable the current installed driver, and then follow this guide

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)


Hope it helps.

---

### Post by undying23 on 2009-04-15
> **Kosimo said:**
> Should be supported by the 180.xx or 185.xx Drivers.
You can give a try to a manual installation if you want.

Just disable the current installed driver, and then follow this guide

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)


Hope it helps.

cool, thanks :D

---

