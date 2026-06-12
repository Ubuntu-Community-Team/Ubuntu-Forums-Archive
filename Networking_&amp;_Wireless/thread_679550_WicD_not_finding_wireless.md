---
title: "WicD not finding wireless"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by zapoqx on 2008-01-27
I checked in various places about this, but I decided to switch to WicD because I couldn't connect to the encrypted wireless connection here at my place.  I install WicD and put a few things on such as the broadcom easy way thing and still nothing.  I have no idea what more I can do.  WicD doesn't even see a wireless signal and I tried changing it from eth1 to wlan0, wlan1, and wlan2.

So I decided to try using that lshw -C network and it sees the wireless, but its labeled "UNCLAIMED" and doesn't seem to have any ownership to it where my wired shows the logical name eth0

So what is the deal?

---

### Post by patrickfromspain on 2008-01-27
could you please post de output of sudo iwlist scan?

thanx

---

### Post by zapoqx on 2008-01-27
Here is the output
 
```
 
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

```

---

### Post by zapoqx on 2008-01-27
Don't usually do this... but someone mind helping?

---

### Post by imdano on 2008-01-28
Looks like you have a driver problem.  Your wireless interface isn't showing up at all.  Whats the output of ```
sudo lshw -C network
```

---

### Post by zapoqx on 2008-01-29
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:05:00.0"]pci@0000:05:00.0[/EMAIL]
       logical name: eth0
       version: 10
       serial: 00:c0:9f:e3:ae:fc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: [EMAIL="pci@0000:05:02.0"]pci@0000:05:02.0[/EMAIL]
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
```
Here it is.

---

### Post by zapoqx on 2008-02-03
Ok.... is someone going to help me? I'm starting to feel ignored here.

---

