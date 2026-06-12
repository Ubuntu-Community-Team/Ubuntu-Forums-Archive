---
title: "Airlink101 AWLL3026 USB causes intermittent freeze on network acquisition under Hardy"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by thirdhaf on 2008-08-27
I've been having an odd problem with my Airlink101 USB wifi card. About 70% of the time after logging in to my account  the computer will freeze up right when a network connection is established. I can tell when this happens because the display usually freezes with nmapplet showing either the signal strength bars or the final connection step. What I mean by freeze is this, the display remains frozen showing the desktop but mouse and keyboard are completely unresponsive.  A hard reboot is required before I can roll the dice on getting a connection again.

I am running Stock Hardy kernel 2.6.24-19 and lsusb gives me:
0ace:1215 ZyDAS WLA-54L WiFi
The problem is definitely with the wifi card since lockups don't occur with the card unplugged or different usb wifi cards plugged in.  I need to use this card because it is the only one I have that supports WPA.

Could someone please help me diagnose this problem? I have no idea where to even start. What can I do to provide useful crash data?

As an aside I want to note that this card is listed as "just works" for Hardy in the wiki linked from the sticky post. Does anyone know of hardware with an OPEN driver that will REALLY be supported? (Either PCI or USB, and supporting WPA)

Thanks in advance

[Update]
The output from dmesg | grep 'zd1211b\? chip' is:

[   52.892027] zd1211rw 5-2:1.0: zd1211b chip 0ace:1215 v4810 high 00-11-a3 AL2230_RF pa0 ---NS

---

### Post by Crafty Kisses on 2008-08-27
That's weird, post the following output of:
```
lshw -C network
```

---

### Post by thirdhaf on 2008-08-27
This is obviously obtained while the card is working normally:

  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: *MAC goes here*
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth2
       serial: *my MAC goes here*
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.10 multicast=yes wireless=IEEE 802.11b/g

---

### Post by thirdhaf on 2008-09-01
This appears to have been a cable issue. Both moving the current cable and replacing it with a new one seems to solve the problems from above.

I still find it odd that a network card malfunction causes my whole system to become unresponsive though.  Can anyone help me pursue this issue?

---

### Post by thirdhaf on 2008-10-17
Quick update.  I was wrong before, my intermittent network failures continue.  Does anyone have any bright ideas?

---

### Post by hari1986 on 2011-12-22
I had the same problem with airlink101 micro usb adapter.

must be too late for this post to appear
nonetheless for other people who are scavenging google and finding message boards

It can be fixed by installing linux-headers-generic (version 2.6.32.37.43)

and also linux-backports-modules for the version of ubuntu you use.

for me, I am using lucid lynx and I installed

linux-backports-modules-wireless-lucid-generic
linux-backports-modules-compat-wireless-2.6.34-2.6.32-37-generic
linux-backports-modules-compat-wireless-2.6.34-2.6.32-36-generic
linux-backports-modules-compat-wireless-2.6.34-2.6.32-31-generic

---

