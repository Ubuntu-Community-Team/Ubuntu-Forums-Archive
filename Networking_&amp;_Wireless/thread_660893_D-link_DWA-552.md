---
title: "D-link DWA-552"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by udoko on 2008-01-07
Want to install 7.10 on Vista machine. Tried the live-CD which saw the DWA-552 adapter. The Network Manager did not see it. Would 7.10 see it properly once I install it and could I get it to work "easily"? Got the Atheros  chip "AR5416" and reading some of the posts it seems that this is incompatible with 7.10. Any ideas would be appreciated. 
Thanks

---

### Post by rfearnle on 2008-02-17
Just picked up a DWA-552 as well. Installed the net5416.inf driver. It is recognized (through lspci) but I can not pick up any signal.

Tried Kwifimanager to no avail-would not detect networks  when I clicked "scan for networks". When I tried to configure Kwifimanager, the  message "unable to detect wireless interface" came up 4 times.

Does anyone know of a solution?

---

### Post by tad1073 on 2008-02-17
[try madwifi](http://madwifi.org/)

---

### Post by rfearnle on 2008-02-19
I've got my DWA-552 working with Ubuntu 7.10. Turns out there was a bug in the version of ndiswrapper I had installed. The following links hold the solution...
[http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/](http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by rfearnle on 2008-02-20
Oh yeah...ya's gots' ta' add ndiswrapper to etc/modules so it will load on boot...forgot to mention that...or actually do it myself. Just noticed when I rebooted last. If you don't you'll have to do the old "modprobe ndiswrapper" every time you reboot.
I can't begin to say how happy I am with Ubuntu. I've been off Window's for 2 weeks now...

---

### Post by munitor on 2008-02-24
I've got my DWA-552 working (after compiling ndiswrapper and installing it), but I can't get out of "g" mode (52 mb/s). Anyone figure out how to get it to go to N mode?

---

### Post by supergumby on 2008-03-02
For those who got it working, could you tell me if you're running 7.10 x86_64? I can't get mine working, neither with ndiswrapper distro version 1.43 or the latest stable version at the moment which is 1.52. I don't have any issue to load the driver into the kernel, but it just doesn't show up in network manager applet or command line. I'm wondering if it might be related to network-manager, I remember when I first started with Ubuntu, I removed network manager and install linux-wlan-ng package to get my USB prism Dlink dwa-122 to work, and it was working fine... :( I've followed what rfearnle was proposing. Any suggestion would be appreciated.

---

### Post by jsym on 2008-03-20
I have a 64-bit machine and the same problem--everything seems to be installed just fine, but I can't get it detected in the wireless manager or by typing iwconfig or ifconfig.

Anyone have any suggestions?

---

