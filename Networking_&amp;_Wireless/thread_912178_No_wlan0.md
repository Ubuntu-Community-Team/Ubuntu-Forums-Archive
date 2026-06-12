---
title: "No wlan0"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by AJB2K3 on 2008-09-06
Ok for some reason I've lost wlan0
```
lshw -C network
```
shows it
```
  description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

```
But yesterday wlan0 just dissapeared.
How do I fix this?

---

### Post by spd106 on 2008-09-06
Your output suggests that the hardware has been found and a driver loaded, but you should also be seeing a second section with the configuration details such as the following.

```
*-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.2 multicast=yes wireless=IEEE 802.11g

```

Have you tried looking at the dmesg log for error messages?

---

### Post by AJB2K3 on 2008-09-07
> **spd106 said:**
> Your output suggests that the hardware has been found and a driver loaded, but you should also be seeing a second section with the configuration details such as the following.

```
*-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.2 multicast=yes wireless=IEEE 802.11g

```

Have you tried looking at the dmesg log for error messages?

I seam to be missing **logical name: wlan0**, Not sure what I'm looking for in dmesg

---

