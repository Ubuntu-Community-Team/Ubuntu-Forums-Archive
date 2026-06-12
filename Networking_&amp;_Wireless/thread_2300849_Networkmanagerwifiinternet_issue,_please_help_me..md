---
title: "Networkmanager/wifi/internet issue, please help me."
date: 2015-10-28
forum: Networking &amp; Wireless
---

### Post by Donald_Trump on 2015-10-28
So I've had ubuntu for a few days now and my internet has been  disconnecting every (anywhere from) 5-45 minutes and theres nothing I  can do, I've tried a few solutions online, they dont work,. it's quite  annoying. 

The Wi-Fi adapter I use is Edimax, someone please help it's very important. Thank you.

---

### Post by kurt18947 on 2015-10-29
Which Edimax? If it's a tiny one - EW-7811Un I think - this will likely fix it. 

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

You can get more info about the network adapter by issuing this command from a terminal:

```

lshw -c net

```

The output should look something like this:

> *-network               
       **description: Ethernet interface**
       [B]product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation[/B]
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 06
       serial: 5c:ff:35:0e:97:a9
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1820(size=32)
  *-network
       [B]description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation[/B]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 35
       serial: 00:23:14:e8:1d:24
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-16-generic firmware=9.221.4.1 build 25532 ip=172.29.206.154 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:f2400000-f2401fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



The bolded text above tell me the vendor and chipset of my wired and wireless networking devices. If my guess about your USB wifi device is correct, the chipset should be RTL8192CU and the vendor should be Realtek. If this is not the case, do not install the fix from Github and copy/paste the output of the "lshw -c net" command here and someone should be able to help you out.

---

