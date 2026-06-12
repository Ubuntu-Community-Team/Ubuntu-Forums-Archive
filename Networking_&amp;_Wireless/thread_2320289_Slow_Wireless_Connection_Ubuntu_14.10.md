---
title: "Slow Wireless Connection Ubuntu 14.10"
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by Rory_Bokser on 2016-04-12
Hi,
I'm still somewhat of a Ubuntu noob. I've had slow connection problems for a while: the number of bars appears to be lower, and slower download/upload speeds than other computers on the same network.

I have tried some prescribed solutions. This one in particular seems to have worked for some, but not for me:
[http://askubuntu.com/questions/470279/internet-slow-on-ubuntu-14-04](http://askubuntu.com/questions/470279/internet-slow-on-ubuntu-14-04)

Here are the results of running [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C network

```
[/FONT][/COLOR]*-network                      description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 6b
       serial: 5c:51:4f:7c:2a:db
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-44-generic firmware=25.228.9.0 ip=192.168.0.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:62 memory:f0400000-f0401fff
[COLOR=#000000][FONT=Ubuntu Mono]
```

[/FONT][/COLOR]Thanks. R

---

### Post by Bucky Ball on 2016-04-12
The bad news is that 14.10 is now old and no longer supported. It hasn't been for awhile. 

Suggest you upgrade to a supported release, 14.04 LTS (supported until 2019), 15.10 (til mid-2016) or wait for the next LTS, 16.04 LTS, which is due in about ten days. 

14.10 has received no updates/upgrades, including security updates, for months. Going online probably not the best idea anyway as the OS is vulnerable as its so out of date.

Good luck. ;)

---

### Post by Rory_Bokser on 2016-04-12
Thanks! Will do the 14.10 -> 15.04 -> 15.10 dance.

---

### Post by Bucky Ball on 2016-04-12
That won't be possible. 15.04 is also dead. You're looking at a clean install. :|

I'd wait until 16.04 LTS and install that (or install now and keep updating/upgrading daily). You seem like someone that might benefit from a version with five years support! :)

For future reference, LTS releases upgrade *directly* to the next LTS release via the net. For instance, 14.04 LTS > 16.04 LTS, leapfrogging

---

