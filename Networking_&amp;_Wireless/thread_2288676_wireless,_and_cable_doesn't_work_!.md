---
title: "wireless, and cable doesn't work !"
date: 2015-07-29
forum: Networking &amp; Wireless
---

### Post by ovidiu4 on 2015-07-29
I'm currently on UBUNTU LIVE VERSION, WITH USB, the installation went good, but NO INTERNET?

So I have cable, and still doesn't connect, but in the live version it does connect.

the wireless doesn't connect at all in live version, or the installed one.

What's is going on here?

I got compaq - hp x7400

please help.

Internet cable,. and wireless doesn't work from fresh install.

---

### Post by PaulW2U on 2015-07-29
*Thread moved to **Networking & Wireless**.*

Re your wireless problem, take a look at the sticky post at the top of this section - [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by ovidiu4 on 2015-07-29
```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:17:08:44:de:5e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.105 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:f4108000-f4109fff
ubuntu@ubuntu:~$
```

---

### Post by Hadaka on 2015-07-29
Hi, from a working wired connection please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe b43
```

---

