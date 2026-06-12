---
title: "wi fi printers"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by micox on 2009-11-03
I've just upgraded to 9.10. I want to get a wireless printer but I'm unsure of brands that would produce a driver for 9.10. Does anyone know?

---

### Post by CAPLinux on 2009-11-03
Micox,

The best place to look is 

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting)

---

### Post by ukripper on 2009-11-03
> **micox said:**
> I've just upgraded to 9.10. I want to get a wireless printer but I'm unsure of brands that would produce a driver for 9.10. Does anyone know?

This one works fine with ubuntu 9.04

[http://www.ebuyer.com/product/159763](http://www.ebuyer.com/product/159763)

---

### Post by DGortze380 on 2009-11-03
> **micox said:**
> I've just upgraded to 9.10. I want to get a wireless printer but I'm unsure of brands that would produce a driver for 9.10. Does anyone know?

A wireless printer shouldn't need a driver on Ubuntu. It will get an IP on your network, then you add a network printer to Ubuntu. I suppose you could run into some issue with the print server on the printer, but I doubt it.

---

### Post by ukripper on 2009-11-03
> **DGortze380 said:**
> A wireless printer shouldn't need a driver on Ubuntu. It will get an IP on your network, then you add a network printer to Ubuntu. I suppose you could run into some issue with the print server on the printer, but I doubt it.

Unless setup software is not Windows only. if setup software runs via browser then he/she ain't gonna have problem at all.

---

### Post by coldReactive on 2009-11-03
> **ukripper said:**
> Unless setup software is not Windows only. if setup software runs via browser then he/she ain't gonna have problem at all.

Lexmark can be "detected" in the cups web browser window, but it can't be used. (IE: x4550)

---

### Post by ukripper on 2009-11-03
> **coldReactive said:**
> Lexmark can be "detected" in the cups web browser window, but it can't be used. (IE: x4550)

Lexmarks are known for pain in the a***

---

### Post by coldReactive on 2009-11-03
> **ukripper said:**
> Lexmarks are known for pain in the a***

I also lucked out on a canon, and got an MP190, which doesn't work out of the box with xsane at all (no, I have to compile a new xsane every time. I can't do this on kubuntu, so when I want to scan, I have to A.) Install Ubuntu, B.) Compile the devshot of xsane-backends with lsusb-dev and C.) run xsane as root.)

Gotta love all-in-one printers.

---

### Post by ukripper on 2009-11-03
> **coldReactive said:**
> I also lucked out on a canon, and got an MP190, which doesn't work out of the box with xsane at all (no, I have to compile a new xsane every time. I can't do this on kubuntu, so when I want to scan, I have to A.) Install Ubuntu, B.) Compile the devshot of xsane-backends with lsusb-dev and C.) run xsane as root.)

Gotta love all-in-one printers.

My canon MP210 works perfectly with drivers provided by canon themselves ([http://software.canon-europe.com/software/0030808.asp](http://software.canon-europe.com/software/0030808.asp)). Even xsane has no problem picking up scanner, scans really good.


These drivers are for 32bit but works under my 64bit 9.04 install with no problem.

---

### Post by coldReactive on 2009-11-03
> **ukripper said:**
> My canon MP210 works perfectly with drivers provided by canon themselves ([http://software.canon-europe.com/software/0030808.asp](http://software.canon-europe.com/software/0030808.asp)). Even xsane has no problem picking up scanner, scans really good.


These drivers are for 32bit but works under my 64bit 9.04 install with no problem.

How do you install them without getting the "This deb package is not for your arch" error?

---

### Post by ukripper on 2009-11-03
> **coldReactive said:**
> How do you install them without getting the "This deb package is not for your arch" error?

You force the architecture to accept 32bit deb like below:
```
sudo dpkg -i --force-architecture ./cnijfilter-common_2.80-1_i386.deb 
sudo dpkg -i --force-architecture ./cnijfilter-mp210series_2.80-1_i386.deb
```

---

### Post by coldReactive on 2009-11-03
What if I can't install a dependency because the distro chooses a different package instead?

IE:
```
ian@Mune:~/Downloads/PixmaMP190/MP190_debian_drivers$ sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb
[sudo] password for ian:
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-common.
(Reading database ... 92551 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_3.00-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
dpkg: error processing cnijfilter-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common
ian@Mune:~/Downloads/PixmaMP190/MP190_debian_drivers$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
ian@Mune:~/Downloads/PixmaMP190/MP190_debian_drivers$ sudo apt-get install --force libcupsys2
E: Command line option --force is not understood
ian@Mune:~/Downloads/PixmaMP190/MP190_debian_drivers$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

---

### Post by ukripper on 2009-11-03
> **coldReactive said:**
> What if I can't install a dependency because the distro chooses a different package instead?

IE:
```
ian@Mune:~/Downloads/PixmaMP190/MP190_debian_drivers$ sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb
[sudo] password for ian:
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package cnijfilter-common.
(Reading database ... 92551 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_3.00-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
dpkg: error processing cnijfilter-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common
ian@Mune:~/Downloads/PixmaMP190/MP190_debian_drivers$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
ian@Mune:~/Downloads/PixmaMP190/MP190_debian_drivers$ sudo apt-get install --force libcupsys2
E: Command line option --force is not understood
ian@Mune:~/Downloads/PixmaMP190/MP190_debian_drivers$ sudo apt-get install libcupsys2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

It asked me to install same dependency and it worked ok for me after i installed that.

---

### Post by coldReactive on 2009-11-03
> **ukripper said:**
> It asked me to install same dependency and it worked ok for me after i installed that.

But it says this when I try to install the depend:

```
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.

```

---

### Post by ukripper on 2009-11-04
> **coldReactive said:**
> But it says this when I try to install the depend:

```
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.

```

As they are old drivers you are trying to install, it depends on old dependency which is libcupsys2 and canon ain't bother to keep up with newest version which is libcups2. Therefore you need to manually install this dependency as below:
go to this link and download libcupsys2 - [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb)

install it by :
```
sudo dpkg -i libcupsys2_1.3.9-17ubuntu3.1_all.deb 
```

after it has installed successfully, you need to follow the initial steps for installing your canon drivers again.

Hope it works out for you.

---

### Post by coldReactive on 2009-11-04
Yes, it works, thank you tons!

---

### Post by ukripper on 2009-11-04
> **coldReactive said:**
> Yes, it works, thank you tons!

Great! For scanner to work you need all 4 debs installed.

---

### Post by disorientedminds on 2009-11-04
I don't know if anyone else has tried this model "HP Officejet 6500 Wireless All-in-One Printer" but it works perfect for me out of the box. I can print and scan with no needed configuration, other than adding the printer. Plus with this model they upgraded the ink capacity in the cartridges to allow for more pages. Hope this helps someone. :D

---

