---
title: "Trouble getting TP-Link wireless usb adapter to work"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by ajmo on 2007-07-15
I [posted this](http://ubuntuforums.org/showthread.php?t=501352) in Absolute Beginner Talk, but go no response so I'll try here.

I just installed xubuntu alternative 7.04 on a celeron 433MHz with 64MB RAM (which I've since upped to 192MB) that used to run W98 (I did a clean install).

Its my first Linux experience, and its fun, except for getting my TP-Link TL-WN321G wireless USB adapter to work. The box said it supported Linux, but there were no drivers.
[http://www.linuxquestions.org/hcl/showproduct.php?product=3778&cat=all](http://www.linuxquestions.org/hcl/showproduct.php?product=3778&cat=all) says that it works.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) doesn't list it, but it is under construction.

I downloaded the RT73 driver from serialmonkey and I seem to have installed it, but when I [FONT="Fixedsys"]$ sudo lshw -C network[/FONT], it doesn't mention a driver (following [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide))

[FONT="Fixedsys"]$ sudo iwconfig[/FONT] shows my rausb0 (but not much info) and Network Settings show the wireless connection with my ESSID (dhcp addressing and I've disabled security).

I can ping the localhost and the IP of the device, but not my router (Netgear DG843G).

The light on the adapter doesn't light up.

I've followed several guides, but don't have much to show for it. 

Any suggestions? Let me know what terminal output you require...

---

### Post by joshuab on 2007-11-16
Hi,

I was able to successfully install this in Gutsy after the same errors as above.  The steps I followed are:

lsmod | grep rt
* to check what drivers were bound to the usbcore and found out that rt2x00usb and others were bound.  I then blacklisted these other driver modules,

sudo vim /etc/modprobe.d/rt2x00usb
* to create a blacklist file for rt2x00usb driver module and type in this line in the file

blacklist rt2x00usb

Repeat for other rt driver modules to ensure that only rt73 is used.

---

### Post by izhar81 on 2008-02-03
I'm still dont know how to do it.

Actually this tplink USB Wifi Dongle have a linux driver.. But i just dont know how to install it.

---

