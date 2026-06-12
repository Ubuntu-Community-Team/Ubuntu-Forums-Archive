---
title: "Wireless card dissapeared in network-manager"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by dvyjones on 2007-06-23
Hi!

I have a Belkin F5D7001 wireless card wich worked before on ubuntu/kubuntu (I downloaded kubuntu-desktop).

But one day I couldn't connect, and I thought it was somethin with linux. I tried to uninstall ndiswrapper and install it again, several times, since none of the tutorials worked. Later I found out the problem was in the router, so I got that fixed, but now the wireless card is gone in network-manager.
Ndiswrapper say that the card is there (hardware present or something)

lspci -n says a lot, but the card I'm using is: 14e4:4320

I have windows installed on the same pc (installed ubuntu with wubi) but that has never been any problem.

How do I get the card back?

And please say what commands I should use (don't just say create a directory ther using root and remove that), because if you don't I'll have to search through the internet for the commands.

---

### Post by spd106 on 2007-06-24
Hello,

This command will tell you which driver is being used for the interface amongst other useful information.
```
sudo lshw -class network
```
and this command is useful to check that ndiswrapper has the right utils version
```
ndiswrapper -v
```

I also suggest that you check whether the bcm43xx driver is blacklisted in the /etc/modprobe.d/blacklist file.

---

### Post by dvyjones on 2007-06-25
The bcm43xx driver is blacklisted, and I'll check the other things you suggested.

---

### Post by dvyjones on 2007-06-25
sudo lshw -class network gave two "*-network"s, a wired one and a wireless one, I'll just include the wireless:

```
*-network UNCLAIMED
description: Network controller
product: BCM4306 802.11b/g Wireess LAN Controller
vendor: Broadcom Corporation
physical id: 9
bus info: pci@05:09.0
version: 03
width: 32 bits
clock: 33 MHz
capabilities: bus_master
configuration: latency=32
resources: iomemory:f0500000-f0501fff irq:11
```

but ndiswrapper is the problem, I think:

```
utils Error: no version specified!
driver modinfo: could not find module ndiswrapper
```

Does that mean I have to download a package named ndiswrapper-utils or something?

---

### Post by dvyjones on 2007-06-25
Now everything works, except that the "Wireless networks" list when i click on the network-manager icon is gone. I tried to connect in KDE with KNetworkManager, but when i tried to enable the card it was just disabled again.

How do I stop that?

---

### Post by dvyjones on 2007-06-28
nobody knows?

---

### Post by dvyjones on 2007-07-01
Sorry for nagging, but I really need to sort this one out

---

### Post by spd106 on 2007-07-01
So you have sorted out the ndiswrapper-utils problem?
I.e. it shows something like this
```
$ ndiswrapper -v
utils version: 1.9
driver version:        1.38
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1

```

and the lshw command used earlier shows something like this
```
  *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@01:0a.0
       logical name: wlan0
       version: 03
       serial: 00:11:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,03/23/2006, 4.40.19.0 ip=192.168.0.10 link=yes multicast=yes wireless=IEEE 802.11g

```

Can you scan for networks using the command line utilities? 
I.e.
```
sudo iwlist wlan0 scan
```

Have you read the NM wiki page? There may something in there that works for you. [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

