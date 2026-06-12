---
title: "Linksys WMP54GS"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by Greensystemsgo on 2007-12-28
Chipset: Broadcom Corporation BCM94306 802.11g (rev 03)
pciid: 14e4:4320
Driver: Linksys [ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe](ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe) (new version)
Other: Ndiswrapper 0.11 and 0.12. Works fine with 64-bit WEP key and WPA supplicant (Fedora core-2, Kernel 2.6.8 and 2.6.9). Use WMP54GS.inf

ok folks im yet another noob. sorry but im so lost at this whole linux thing, but im tired of bill gates' crappy xp. so im done.  i cant seem to get my wifi card working.  Ive gotter v1.1 drivers, and even the newest drivers via that link. ive extracted the correct drivers from the windows auto install like i should, but thats where it stops.

I cant for the life of me get NDISwrapper installed. the code my buddy told me to use is as follows
```

sudo apt-get install ndiswrapper-utils

sudo ndiswrapper -i ~/Desktop/WUSB54G.inf

sudo ndiswrapper -m

for conffile in /etc/ndiswrapper/WUSB54G/*.conf; do

sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile


```

however after typing in the very first line, it errors out.

```

sudo apt-get install ndiswrapper-utils
Reading Package lists... Done
Building dependency tree
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
However the following packages replace it:
     ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate

```

any help/pointers? im dead stuck. 

I dont have LAN, I NEED MY WLAN!

---

### Post by Greensystemsgo on 2007-12-28
i have the firmware in resticted drivers, but when i go to install it, it comes up with an error :(  "bcm43xx-fwcutter" is not enabled

---

### Post by ndube on 2007-12-28
Try the following command.

sudo aptitude install ndiswrapper-common

---

