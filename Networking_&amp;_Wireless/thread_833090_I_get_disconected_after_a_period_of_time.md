---
title: "I get disconected after a period of time"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by alek66 on 2008-06-18
It s  really hard thing to explain:

I am at work, using GOS space. its a Toshiba a10, with a pmcia linksys card. Whenever i am on wifi... after some time I get disconnected from any of the to different wifi routers (also linksys) we have here. This happens even faster if i am using bit torrent, or playing some game on the network.

What log can I post so you can understand better my problem.

---

### Post by dmizer on 2008-06-19
posting the output of:
```
iwconfig
```
and
```
lshw -C network
```
will be helpful.

also, just after you're disconnected, take a look at the dmesg output:
```
dmesg | tail
```

it's not much, but it's a start and better than nothing.

---

### Post by alek66 on 2008-06-19
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"tao-it"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0F:66:19:19:19   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=56/100  Signal level=-68 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:654102  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:8f:20:f5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 03
       serial: 00:0c:41:bb:30:1c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=10.0.0.72 latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

Wil post the other on disconnection

---

### Post by Zalbor on 2008-06-19
Are you using 8.04?
I had that problem with 7.10, it got fixed with 8.04...

---

### Post by alek66 on 2008-06-19
> **Zalbor said:**
> Are you using 8.04?
I had that problem with 7.10, it got fixed with 8.04...

Gos cant be update to 8.04 yet...

---

### Post by dmizer on 2008-06-19
> **alek66 said:**
> Gos cant be update to 8.04 yet...

that's really a shame, because hardy has much better drivers for your particular card.

if you continue to have the problem, you may want to look into ndiswrapper.

---

