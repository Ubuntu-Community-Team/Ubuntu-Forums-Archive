---
title: "do I need drivers for my hp compaqnc6230 to access my wireless network"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by N0_0ne on 2007-10-01
I just installed ubuntu 6.06 on my hp notebook, when trying to access the internet I have an on/off swith on my wireless card and the light isnt on whether I click it or not, leading me to believe its a driver issue. When I go to hp.com and try to get my drivers ubuntu isnt in the os droplist, what should I do?

Im a noob so it could be something stupid, if so please forgive me, thanks for your time

---

### Post by Lambert on 2007-10-01
Open a terminal and type in the following command.

```
sudo lshw -C network
```You should get output similar to this.

 ```
*-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@04:02.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:0d:b4:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.0.174 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:a8401000-a8401fff irq:22

```This will tell if your hardware is recognized and a driver is loaded for it.

In looking at the [wiki page]("https://wiki.ubuntu.com/LaptopTestingTeam/HPCompaqnc6320?highlight=%28laptop%29") for this laptop, it's marked that wireless works.

---

