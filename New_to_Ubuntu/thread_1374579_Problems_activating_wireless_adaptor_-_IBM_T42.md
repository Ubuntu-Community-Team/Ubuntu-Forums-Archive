---
title: "Problems activating wireless adaptor - IBM T42"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Vin75 on 2010-01-07
Hello All,
Firstly, this is my very first Linux installation. I am planning on learning more as time passes, but I am as "green" as Newbies come...
I have just installed Ubuntu 9.1 on my IBM T42 Laptop on a 10 GB partition - I am dual-booting with Windows XP, where the wireless adaptor functions fine and can find my home wireless network. When I log into Ubuntu, I cannot turn on the wireless adaptor. I have set it up correctly, as on one fluke, the laptop connected to the wireless network automatically but since then, I have had no luck with turning on the wireless adaptor.
Any ideas?

My apologies for not posting this earlier..... lshw -C network output:

 *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:17:9d:d7
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 mingnt=255 multicast=yes
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8400(size=64) memory:c0240000-c024ffff(prefetchable)
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:14:a4:0e:96:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0214000-c0217fff memory:c0400000-c07fffff memory:c0800000-c09fffff(prefetchable)

---

