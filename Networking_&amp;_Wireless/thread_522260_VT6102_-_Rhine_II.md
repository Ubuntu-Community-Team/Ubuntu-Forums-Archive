---
title: "VT6102 - Rhine II"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by metalix on 2007-08-10
Fujitsu-Siemens AMILO V3515

Kubuntu seems to detect my driver:

When I type the command "lshw -C network" into the terminal, I get:

```
*-network
 description: Enternet interface
 product: VT6102 [Rhine-II]
 vendor: VIA Technologies, Inc.
 physical id: 12
 bus info: pci@00:12.0
 logical name: eth0
 version: 7c
 serial: 00:14:0b:0b:a1:a2
 width: 32 bits
 clock: 33Mhz
 capabilities: bus_master cap_list ethernet physical
 configuration: broadcast=yes driver:via_rhine driverversion=1.4.2 latency=24 maxlatency=8 mingnt=3 multicast=yes
 resources: ioport:6800-68ff iomemory:c9400400-c94004ff irq:21
*- network DISABLED
 description: Wireless interface
 product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
 vendor: Broadcom Corporation
 physical id: 1
 bus info: pci@05:01.0
 logical name: eth1
 version: 02
 serial: 00:la:73:0b:1b:8d
 width: 32 bits
 clock: 33Mhz
 capabilities: bus_master ethernet physical wireless
 configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
 resources: iomemory:c9100000-c9101fff irq:22
```

Does anyone have any idea how I can enable the device?

Lewis

---

### Post by icod on 2007-10-11
Same kernel, same here
I'm also looking for a sollution
It's the only nic, and it's onboard , an asus 600-x mobo
no wireless card tho

in more detail, the router doesn't "see" the network card, e.g. link is not up, it's not a cable problem, same 2 cables work when connected to a different pc and laptop

does anyone know if this problem also exists in debian or is it ubuntuspecific

and no sorry i can't post a dmesg, lspci or similar
oh well back to gentoo

---

### Post by gombong on 2007-10-24
same here;

i am installing ubuntu (gutsy) for my friend desktop. ubuntu automatically installed via-rhine driver for this machine. The network manager applet shows that the link is up, however somehow the card unable to get ip address.

Please help. Need at least to unable the wired network b4 I am able to solve the wireless which is another problem altogether.

Thks

---

### Post by overclucker on 2008-02-22
same problem here. feel to post helpful hints for diagnosing, as well as the  possible solutions to our problem . . . any cool dinner ideas would be good too. . .

---

### Post by Cybercool on 2008-03-22
If you want the VT6102 to work, you must start ubuntu with the boot option: acpi=noirq

Then dhcp will work

---

