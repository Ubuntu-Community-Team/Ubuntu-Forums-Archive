---
title: "wireless don't work"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by trocchietto on 2008-11-04
Hallo everyone

my wireless connection don't work. There are several days I don't understand the reasons

if I do sudo iwconfig it appears that eth1 is up
it says Access point: not associated
 lsmod recognize an ipw220 I would like to connect at internet.
The howto's in internet don't help me
and network-admin don't works):P

---

### Post by superprash2003 on 2008-11-04
please post output of lshw -C network from the terminal

---

### Post by trocchietto on 2008-11-04
> **superprash2003 said:**
> please post output of lshw -C network from the terminal

here it is;)

  *-network:0
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:c4:ff:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:c0:9f:7f:6a:9f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5788-v3.01 latency=32 mingnt=64 module=tg3 multicast=yes

---

### Post by trocchietto on 2008-11-06
:popcorn:anytips?

---

### Post by superprash2003 on 2008-11-06
are you on ibex?? have you tried system->admin->hardware drivers?

---

