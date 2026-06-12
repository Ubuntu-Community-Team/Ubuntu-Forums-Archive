---
title: "Dell XPS M1330 + Broadcom + 8.04"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by xkaliburx on 2008-05-18
Well I have just restaged the laptop from Fedora (used for years) to give U a shot.  I have the newest version, About shows it as Ubuntu 8.04 - the Hardy Heron.

If you google ubuntu broadcomm, etc. you get 1000's, 99.9% show using ndiswapper, but is 8.04 different.  Alot of the older threads say the device isn't found, etc. but System -> Administration -> Hardware Drivers shows the BroadCom B43 wireless driver and in use.  It seemed to download the firmware, but nothing worked.  I used a great wireless app for fedora called wlassistant which did load, but I don't see any wireless networks (I have 4 right around the house.)  Running from a terminal shows this in the back;
scan: /sbin/iwlist wlan0 scan
No networks found!

Reading the initial sticky post shows;
lshw -C network
*-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:4c:5a:24:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

So, I am not really sure if 8.04 needs the ndiswrapper installed to use the windows drivers as it looks like it doesn't, and even though linux is linux, each distro is a bit different, so any help / advice on getting someone to change over to Ubuntu is appreciated.

Not sure if I need to provide more info, so I will dump out a few more things that might help;
 sudo lspci | grep Broad
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

Anything else could help, let me know what (and maybe how)

Lr

---

