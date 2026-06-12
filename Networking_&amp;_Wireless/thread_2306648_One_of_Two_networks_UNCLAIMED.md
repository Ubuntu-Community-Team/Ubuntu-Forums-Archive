---
title: "One of Two networks UNCLAIMED"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by lu333031 on 2015-12-17
I have a system with 2 ethernet ports (and hence 2 network cards). Does the following output from 

```
sudo lshw -C network
```

indicate that the UNCLAIMED network card is bad (i.e., some HW problem)?

```

  *-network UNCLAIMED
       description: Ethernet controller
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:fe9e0000-fe9fffff ioport:dc00(size=32) memory:fe9dc000-fe9dffff
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 00
       serial: 00:30:18:a8:6f:eb
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=2.1-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:19 memory:feae0000-feafffff ioport:ec00(size=32) memory:feadc000-feadffff

```

I can send the system back to the vendor under warranty.

Thank you.

Lu

---

### Post by SeijiSensei on 2015-12-17
No, I think it just means that it isn't configured with an address.  Is one interface connected to a network but the other one not?

You can easily check by running
```
sudo ifconfig ethX up
```
replacing "X" with "0" or "1" as appropriate.  After you bring up the interface try assigning it an address manually with:
```
sudo ifconfig ethX 10.10.10.10 netmask 255.255.255.0
```

It would be extremely rare for a machine with a failed adapter to leave the factory.

---

### Post by lu333031 on 2015-12-17
I have an identical ("Good") system and do not see an UNCLAIMED network card on it. "lshw" is executed without any ethernet cable connected on both systems (either port). 

When I do connect an ethernet cable to either port of the "Good" system, I get a pop-up msg "Wired connection X, connection established" (X = 1, 2).

With the ("Bad") system with an UNCLAIMED network, I get the popup msg with only one port. Nothing happens when the cable is connected to the 2nd ethernet port. On the "Bad" system,

```
sudo ifconfig ethX up
```

returns nothing for X=0 and returns the following for X=1

```
eth1: ERROR while getting interface flags: No such device
```

With the ("Good") system. ifconfig returns nothing for X=0 and 1.

---

### Post by nmcnulty on 2016-08-19
Hi, 

Was this ever solved? I am having the same exact issue.  My drivers appear to be loaded fine as eth0 is up with that driver (exact same hardware), but the second NIC - what should be eth1 - is UNCLAIMED.  Since it is, I cannot assign any IPs to it or change status. Any tips are appreciated.

$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:22:4d:b5:f5:e8
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.3.4-NAPI duplex=full firmware=2.1-2 ip=192.168.1.38 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:d0220000-d023ffff memory:d0200000-d021ffff ioport:2000(size=32) memory:d0240000-d0243fff
**  *-network UNCLAIMED**
       description: Ethernet controller
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:d0100000-d011ffff memory:d0000000-d00fffff ioport:1000(size=32) memory:d0120000-d0123fff

---

