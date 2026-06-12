---
title: "NIC comes up with autonegotiation off: why and how to fix?"
date: 2018-10-08
forum: Networking &amp; Wireless
---

### Post by henrylaw on 2018-10-08
I am building an 18.04.1 server with three network interfaces, one on-board and two add-on NICs.  It's an old machine so one of the NICs is PCI-e and the other PCI.  All three interfaces are connected to gigabit capable switches.

The onboard interface and the PCI-e card come up with autonegotiation on but the PCI card (enp4s0) comes up as half-duplex 10Mb/s, which isn't improving performance much:
```
~$ sudo ethtool enp4s0
Settings for enp4s0:
        ...
    Supports auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Half
    ...
    Auto-negotiation: off
```
Extract from lshw -class network:```

*-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 10
       serial: 00:e6:a8:16:ec:ee
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=10.18.78.254 latency=64 link=yes maxlatency=32 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:e800(size=256) memory:fbe00000-fbe000ff
```
Of course I can take an ethtool crowbar to it and set it to the right settings, but that's untidy.  Questions:

[LIST=1]
[*]How can I find out why it's coming up with auto-negotiation off and fix it? 
[*]If I have to set it myself (not the worst thing in the world) can I make netplan do it via yaml?  Googling suggests not.  If not, then what's the preferred way to do it?  Options seem to be writing a service to do it before network.online or putting an ethtool command in /etc/rc.local. 
[/LIST]

---

### Post by praseodym on 2018-10-08
```
sudo ethtool -s enp4s0 speed 1000 autoneg on
```
should do the trick. You need to set 2 parameter, so if 10 shall be used, then its

```
sudo ethtool -s enp4s0 speed 10 autoneg on
```

---

### Post by henrylaw on 2018-10-08
Mmm, yes.  When I said "putting an ethtool command in /etc/rc.local"  that's what I had in mind.  But that shouldn't be necessary; the other  two NIC's come up with autonegotiation on, as they should.  I'm hoping  to find why autonegotiation has been turned off and fix that fault,  rather than put something in later to counter it.

---

