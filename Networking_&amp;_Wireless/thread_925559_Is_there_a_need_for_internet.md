---
title: "Is there a need for internet"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by F8M on 2008-09-20
I need to install the ndiswrapper wireless driver, but I don't have internet. Can this be done. And if not, can I download the commands for it to be burned on a CD. The following info. is what I gathered so far:
- Compaq Presario V6000 Notebook
- Broadcom Corp. BCM4311 802.11 b/g WLAN (Rev. 01)
- Ubuntu 8.04.1
- Kernel/Architecture: 2.6.24-19-generic-i686 
Can somebody help me. THANKS

---

### Post by tacticalbread on 2008-09-20
you could download the packages, and install it with them.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndiswrapper](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndiswrapper)

---

### Post by jualin on 2008-09-20
You don't need internet to install Ndiswrapper in your computer. Just make sure to use the Ubuntu Live CD as your Repository. To do this open Synaptic Package Manager, under System, Administration. Then click on Settings, Repositories. and enable the "Cdrom with Ubuntu 8.04" box. Then Reload your repositories. And search for Ndiswrapper and install it. 
After you install Ndiswrapper you will need the driver for your Wireless Card. First you need to identify your wireless card by going to the terminal and typing > lspci
lspcmcia and according to what you posted it should read "Broadcom BCM4311...". Then lookup in the forums for help on how to install the wireless driver using Ndiswrapper or use the tutorial found on my signature (Ndiswrapper). Hope this helps!

---

### Post by jualin on 2008-09-20
> **tacticalbread said:**
> you could download the packages, and install it with them.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndiswrapper](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ndiswrapper)

The packages are found on the Ubuntu Live CD, so there is no need to download them.

---

### Post by Ayuthia on 2008-09-21
There are also two other options:
b43:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
Go to Option 2 to find out how what to download and install the files when you don't have an internet connection in Ubuntu.

wl:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
This is the Linux wireless module from Broadcom.  It does work with the 4311 rev 01 card but does have problems with ssh and remote connections to mysql.

You might try doing the b43 route first because it is just a firmware download.  It does not require any additional configuration like the ndiswrapper or wl route.  If it does not work, then try the other two options.

---

### Post by F8M on 2008-10-04
Now that I have a free weekend, I tried the steps you mentioned. After re-enabling the "Cdrom with Ubuntu 8.04" box in the Synaptic Package Manager, I got the following error message; 
"W: Failed to fetch cdrom:[Ubuntu 8.04 Hardy Heron - Release i386 (20080702.1)]/dists/hardy/main/binary i386/Packages.gz Please use apt cdrom to make this CD-Rom recognized by APT.apt-get update cannotbe used to add new CD-ROM."
"W: Failed to fetch cdrom:[Ubuntu 8.04 Hardy Heron - Release i386 (20080702.1)]/dists/hardy/restricted/binary i386/Packages.gz Please use apt cdrom to make this CD-Rom recognized by APT.apt-get update cannotbe used to add new CD-ROM."
So then I decided to install it straight from the CD ("ndiswrapper-utils-1.9 1.50 lubuntu1 i386.deb"). It responded by saying that it was already istalled. Can you me with this. THANKS

> **jualin said:**
> You don't need internet to install Ndiswrapper in your computer. Just make sure to use the Ubuntu Live CD as your Repository. To do this open Synaptic Package Manager, under System, Administration. Then click on Settings, Repositories. and enable the "Cdrom with Ubuntu 8.04" box. Then Reload your repositories. And search for Ndiswrapper and install it. 
After you install Ndiswrapper you will need the driver for your Wireless Card. First you need to identify your wireless card by going to the terminal and typing  and according to what you posted it should read "Broadcom BCM4311...". Then lookup in the forums for help on how to install the wireless driver using Ndiswrapper or use the tutorial found on my signature (Ndiswrapper). Hope this helps!

---

### Post by cariboo on 2008-10-04
Make sure you have ndiswrapper-common and ndisgtk installed also. Ndisgtk is a gui  frontend for ndiswrapper.

Jim

---

