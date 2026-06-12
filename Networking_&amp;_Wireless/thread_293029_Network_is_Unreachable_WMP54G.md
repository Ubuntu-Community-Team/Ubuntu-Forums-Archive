---
title: "Network is Unreachable WMP54G"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by yet another newbie on 2006-11-04
Please help a newbie. I've installed Linksys WMP54G in Ubuntu. The card is recognized as is the driver (rt61). I've configured it for DHCP and can scan for networks and locate multiple access points (2 of mine, 6 other neighbors). I do have WEP enabled, but I've tried removing WEP with the same results. If I try to ping my router 192.168.46.1 I receive Network is Unreachable. If I use dhclient I see the request for IP but it's never answered. I've also tried static IP.

Do I need another driver and NDISwrapper?

Thanks in advance for your time and help.

---

### Post by yet another newbie on 2006-11-04
> **yet another newbie said:**
> Please help a newbie. I've installed Linksys WMP54G in Ubuntu. The card is recognized as is the driver (rt61). I've configured it for DHCP and can scan for networks and locate multiple access points (2 of mine, 6 other neighbors). I do have WEP enabled, but I've tried removing WEP with the same results. If I try to ping my router 192.168.46.1 I receive Network is Unreachable. If I use dhclient I see the request for IP but it's never answered. I've also tried static IP.

Do I need another driver and NDISwrapper?

Thanks in advance for your time and help.

I've been working on this wireless situation for more than a week. 3 different cards all get to the same point one way or another. I've used ndiswrapper, blacklisted bcm43xx, then re-installed ubuntu started over with another card. I went and purchased this particular card because of the hardward list on this forum and others. I find it hard to believe that it should be this difficult. I'll have to keep this load for the next 7 weeks for school, but I think I'm losing my enthusiasm for ubuntu.

---

### Post by FrodoB on 2006-11-04
Run lspci and verify that your device is:

Vendor:1814 dev:0201

If so, go to the Ralink web site and download the RT61 driver from their support section.  Read the readme file and make sure that you install the firmware as prescribed.

If your card is different, then report the information back to the group.

You can check your devices at:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

FrodoB

---

### Post by yet another newbie on 2006-11-05
Thanks for your response apparently my device is 0301

kim@Ubuntu:~$ sudo lspci -v | grep Network
0000:02:0a.0 Network controller: RaLink: Unknown device 0301

Subsystem: Linksys: Unknown device 0055
0000:02:0a.0  1814:0301

kim@Ubuntu:~$ sudo lshw -C Network
  *-network
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: a
       bus info: pci@02:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=rt61
       resources: iomemory:feaf8000-feafffff irq:3
  *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:18:39:18:0b:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT61 Wireless

---

### Post by yet another newbie on 2006-11-05
Just an update --- thanks to judgekaster's post I'm updating this forum via Ubuntu not Windows. I had the No DHCPOFFERS Received problem.

For others here is the link to the thread:
[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

---

### Post by FrodoB on 2006-11-05
So you have solved your issue then?

---

### Post by yet another newbie on 2006-11-06
Yes, I haven't been able to get the boot up script to run without errors yet, but at least I know how to get the connection once the desktop loads. I'll fix the script later.

---

