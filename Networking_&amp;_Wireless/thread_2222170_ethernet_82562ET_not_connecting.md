---
title: "ethernet 82562ET not connecting"
date: 2014-05-05
forum: Networking &amp; Wireless
---

### Post by garyzw on 2014-05-05
Just installed Xubuntu on my wife's PC the wireless connectinion works intermitenly but need this to be wired, ran the sudo lshw -C network comand and got the following output... I have no clues as to what it means. I want to remove the wireless coneection completely.  

```
 
[sudo] password for angela: 
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 03
       serial: 00:13:20:6b:e2:c7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:dfaff000-dfafffff ioport:c8c0(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:f2:57:21:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwlhigh5 driverversion=1.59+Netgear,03/28/2011, 5.100.6 ip=192.168.2.7 link=yes multicast=yes wireless=IEEE 802.11
```

---

### Post by mörgæs on 2014-05-05
If you don't want the wireless connection why did you install Ndiswrapper?

---

### Post by garyzw on 2014-05-05
> **mörgæs said:**
> If you don't want the wireless connection why did you install Ndiswrapper?

As I said the wireless connection works intermittently for what ever reason. Did you read my post?
It is not that I don't want the wireless connection-- I would rather use that but since it is not working properly I'm going to go wired. DO you have any suggestions?

---

### Post by mörgæs on 2014-05-06
Yes, I have one: Another posting style will make it more likely that people are going to help you.
Signing out.

---

### Post by garyzw on 2014-05-06
> **mörgæs said:**
> Yes, I have one: Another posting style will make it more likely that people are going to help you.
Signing out.

What is the problem with my posting style? Why so rude?

---

### Post by voidofone on 2014-05-06
garyzw: pre-check steps if you have not done them already: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers)

Also, check out this list that I found: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?joomla/index.php](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?joomla/index.php)
You may have to determine what hardware you actually have to determine compatibility.

additional reference:[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by garyzw on 2014-05-06
I have the Netgear N300 Wireless USB Adapter which works on boot for a few minutes then it loses connection. I have to either reboot or unplug the Wireless USB Adapter and then I have a good connection again for a few minutes. I ran a Cat5 to the computer but can't seem to get it to switch from the wireless to the cat5. The Netgear N300 Wireless seems to be installed correctly since it is working intermittently.

---

### Post by voidofone on 2014-05-09
Check out the universal Broadcom STA driver if you haven't already. Link:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Also referencing an old thread but should be mostly relevant with steps to take:
[http://www.linuxquestions.org/questions/linux-hardware-18/netgear-wn311b-wireless-pci-adapter-and-wireless-connection-876693/](http://www.linuxquestions.org/questions/linux-hardware-18/netgear-wn311b-wireless-pci-adapter-and-wireless-connection-876693/)

Hope it helps.

---

### Post by garyzw on 2014-05-09
Thanks voidofone--thats got it :)

---

