---
title: "Dualboot Ubuntu WiFi much slower than Windows"
date: 2019-08-10
forum: Networking &amp; Wireless
---

### Post by ahoch12 on 2019-08-10
Hi Ubuntu community, first post here so I apologize in advance if it's in some way incorrect. 

I started dual-booting ubuntu on my Lenovo Thinkpad and the WiFi is much slower than on the Windows partition. Windows speeds are about 40Mbps while Linux speeds are 10Mbps at best and sometimes barely work at all. 

I've been reading through many of the other threads on this topic but can't seem to solve this issue--the recommendations I see are usually personalized to the OP's equipment and I don't want to go around changing settings willy-nilly without understanding what going on.

Many thanks in advance.

Here's my [B]lshw -C network
[/B]```
WARNING: you should run this program as super-user.  *-network               
       description: Ethernet interface
       product: Ethernet Connection (3) I218-LM
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 03
       serial: 50:7b:9d:0e:ba:c9
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.2-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:e1200000-e121ffff memory:e123e000-e123efff ioport:3080(size=32)
  *-network
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 59
       serial: 4c:34:88:05:f0:37
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-38-generic firmware=22.391740.0 ip=192.168.1.154 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:46 memory:e1000000-e1001fff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:2
       logical name: enp0s20u2c4i2
       serial: de:0c:5c:c1:09:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes

WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by ahoch12 on 2019-08-17
Some updates:

Turning off wifi powersave seemed to have helped the worst issues, but still can't get Mbps above 10. 

Doing the 11n_disable=8 hack (below) made it worse, so I undid it

> 
[COLOR=#2E8B57][FONT=Monaco]echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi11n.conf[/FONT][/COLOR]

These instructions were found [here]("https://forums.linuxmint.com/viewtopic.php?t=239854")

---

### Post by jeremy31 on 2019-08-17
I would update to a supported kernel, 4.10 has been out of support for at least a year

---

### Post by ahoch12 on 2019-08-18
> **jeremy31 said:**
> I would update to a supported kernel, 4.10 has been out of support for at least a year

Thanks for the tip jeremy31! I updated to **driverversion=4.15.0-58-generic** and was able to achieve 15Mbps, however some more runs of the speed test average about 10Mbps and this is still far short of the 40Mbps I see on Windows. Is there anything else you'd recommend?

---

### Post by jeremy31 on 2019-08-18
I would try the 11n_disable=8 again and reboot

---

### Post by ahoch12 on 2019-08-19
> **jeremy31 said:**
> I would try the 11n_disable=8 again and reboot

Upload Mbps gained a lot (from 10 to 20) -- Download Mbps seems a couple Mbps better. Progress for sure but still not near Windows :/

---

### Post by jeremy31 on 2019-08-19
See the wireless script link in my signature and post results

---

### Post by ahoch12 on 2019-08-20
[https://paste.ubuntu.com/p/VNPSC3kStQ/](https://paste.ubuntu.com/p/VNPSC3kStQ/)

---

### Post by jeremy31 on 2019-08-20
Can you change your wifi router to use channel 6?

---

### Post by ahoch12 on 2019-08-21
> **jeremy31 said:**
> Can you change your wifi router to use channel 6?

This bumped it up to 35 Mbps! (and 45 Mbps on Windows)

Thanks so much for your help. Even if this is as good as it's going to get, it's a huge win.

---

