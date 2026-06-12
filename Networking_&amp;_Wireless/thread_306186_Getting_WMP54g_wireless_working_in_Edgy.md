---
title: "Getting WMP54g wireless working in Edgy"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by justsee on 2006-11-24
I've only just jumped on the Linux / Ubuntu bandwagon in the last few days, and purchased a WMP54g (RT2561/RT61 chipset) wireless card on the basis that it worked fine under linux. Over the last two days I've definitely been in a 'this ain't happening!' mindset, frustrated beyond belief as a total newb struggling to get an essential part of my machine working. To discover that something so central apparently broke between Dapper and Edgy almost had me jumping back to XP or at least Dapper, but just at the last moment a solution presented itself! I'm very happy now :-)

Here are the steps I had to take from a clean install of Edgy in case this helps anyone:

* System -> Administration -> software sources to tick universe and multiverse
* sudo apt-get install sysutils
* sudo apt-get install linux-headers-`uname -r`

The following instructions were taken from [here]("http://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117/comments/11") and mentioned in '[Edgy Known Issues]("http://wiki.ubuntu.com/EdgyKnownIssues")' under Wifi cards:
* download the Linux RT61 driver (ralink.com site seems to have disappeared!!! This is a link to mirrored file) [this file]("http://gentoo.osuosl.org/distfiles/RT61_Linux_STA_Drv1.1.0.0.tar.gz") (original link in instructions doesn't work)
* tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz
* go to /tmp/RT61_Linux_STA_Drv_x.x.x.x.tar.gz/Module directory
* cp Makefile.6  ./Makefile
* make all
* I then had to create the directory /etc/Wireless/RT61STA/
* cp rt2561.bin /etc/Wireless/RT61STA/
* cp rt2561s.bin /etc/Wireless/RT61STA/
* cp rt2661.bin /etc/Wireless/RT61STA/
* dos2unix rt61sta.dat (why initially need to install sysutils)
* cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat
* sudo su
* /sbin/insmod rt61.ko
* depmod -a
* modprobe --remove rt61pci
* gedit /etc/modprobe.d/blacklist and added: blacklist rt61pci
* gedit /etc/modules and added: rt61
* gedit /etc/modprobe.d/aliases and added: alias ra0 rt61
* gedit /etc/network/interfaces and added:
iface ra0 inet dhcp
wireless-essid YOURESSID
auto ra0
* sudo ifconfig ra0 up

and it should work. I just setup my network with no encryption to get it working first, but once WPA or WEP needs setting up this is all done simply in rt61sta.dat

These are rehashed / combined instructions from a total linux newb, so if there's a simpler way or I've missed anything in these notes let me know!

Hope it helps someone.

I've also noticed since posting this that there are a lot of (better / more detailed) existing posts on this that I somehow didn't find via search / google:
[HOWTO: RT61 on Egdy Eft with WP]("http://www.ubuntuforums.org/showthread.php?t=296822")
[RaLink RT61 Wireless Solved]("http://www.ubuntuforums.org/showthread.php?t=132980")

---

### Post by eoinmadden on 2007-01-07
Why are you blacklisting the rt61pci module?

---

