---
title: "Ubuntu studio help with interenet."
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Mmarzex on 2008-12-05
I need to get interent started on an acer aspire 5100 I already know that I have to install network-manager but you need the net to do which I don't have on that laptop. Then I tried the shell connect way but I don't know how to find the name of my wireless card on there.

Please help.

---

### Post by Hume's doona on 2008-12-05
it may work if you use a cable just the first time to configure it. after that it should automatically connect to your router on boot up.

I'm an ubuntu noob too, but in both fedora and suse, the ethernet cable connection was eth0 and wireless was eth1. 

i haven't configured my wireless yet... i'm still virtualising, but the cable connection is eth0 in ubuntu studio, but it hasn't found my wireless card on my macbook pro

i hope that helps a bit

---

### Post by Mmarzex on 2008-12-05
I just need to know how to find out what the name is I can't find out it says my wireless card is installed but I don't know what it is

---

### Post by flanagan on 2008-12-05
From a terminal, issue the command *lshw* and look for something like:

```
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:33:55:c6
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200
driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005
ip=192.168.0.193 latency=64 maxlatency=24 mingnt=3 module=ipw2200
multicast=yes wireless=IEEE 802.11g
```

---

