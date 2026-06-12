---
title: "problems with US robotics gigabit ehternet card"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by krauser530 on 2007-08-02
i recently purchased a new gigabit Ethernet card in hopes of improving the speed of my internet, but it performs slower than a 100mbps card. When running ethtool i recieve the following results.

Settings for eth3:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

I am relatively new to ubuntu and networking configurations. Any ideas on how i can switch this to full duplex and at least 100mbps?

---

### Post by Tyggna on 2007-08-02
Looks like it sees your Network card capabilities, but that the connection coming IN to your computer is at 10mbps at half duplex.   It'll auto-configure to the lowest active connection speed.  If you're running anything at 10mbps, it'll throttle you down.


This link might be more helpful:

[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

---

### Post by krauser530 on 2007-08-02
so if i have another computer running at slower speeds on the network it will slow down to that speed on every computer?

---

### Post by Tyggna on 2007-08-02
> **krauser530 said:**
> so if i have another computer running at slower speeds on the network it will slow down to that speed on every computer?

slow down your router/switch whenever your communicating with it, yah.

---

### Post by krauser530 on 2007-08-02
that sucks. thanks for the help

---

### Post by noob12 on 2007-08-02
It's not as bad as that.  Modern over-the-counter gigabit switches will handle a mix of clients at various link rates.  The switch will do buffering and flow control to regulate between attached hosts that have different link rates.  So two fast hosts will communicate at fast rates.  You're only dragged down when you communicate with a slow host.

Tell us what kind of switch you are connecting to (model, version).   Assuming you are running modern equipment supporting at least 100mbps, seeing 10mbps as we do in your **ethtool** output is a sign of an autonegotiation failure, possibly a bad cable, otherwise a driver bug.

If you post the output of ```
lshw -C network
``` This will tell us a bit more about the equipment and driver.  I can tell you if I've seen this problem with the same hardware/drivers.  

Personally, I have had similar problems with the drivers on my gigabit card negotiating a full 1000mbps link rate with my gigabit switch.  I haven't seen this on Fedora boxes with similar hardware connecting to the same switch, and I haven't see it on Windows.  I solved my problem by adding **pre-up** lines in my **/etc/network/interfaces** to set the link rate and duplex and it runs just fine;  I can achieve roughly 700+ mbps in practice between two of my gigabit clients with jumbo frames.  Don't expect fast Samba transfers in Nautilus though.  There's some bug there.

Assuming it is a 10/100 switch, you'll only be able to set the link rate up to 100mbps.   You can manually set the link rate to 100mbps and duplex as follows.  I've put eth3 here based on your earlier output.
```

ethtool -s eth3 speed 100 duplex full autoneg off

```
You can guess what it would be for 1000mbps, but note that it won't work right unless you have a gigabit switch.

I'll follow this thread a bit longer if you post back.

---

### Post by krauser530 on 2007-08-12
my computer has 2 cards built in and a third that ive added.
don't ask why so many cause its a long story.
the card in question is the US Robotics USR997902 10/100/1000 Mbps PCI Network Card

sorry if this may sound stupid, but how can I tell what the speed of my switch is?
and what are pre-up lines?

the output of lshw -C network is:

lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:15:f2:b2:5b:20
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:dc00-dcff iomemory:fddff000-fddff0ff irq:21
  *-network:1
       description: Ethernet interface
       product: USR997902 10/100/1000 Mbps PCI Network Card
       vendor: U.S. Robotics
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth1
       version: 10
       serial: 00:14:c1:32:4e:40
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.6 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:da00-daff iomemory:fddfd000-fddfd0ff irq:17
  *-network:2
       description: Ethernet interface
       product: LNE100TX
       vendor: Lite-On Communications Inc
       physical id: a
       bus info: pci@02:0a.0
       logical name: eth2
       version: 20
       serial: 00:a0:cc:50:97:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 latency=64 multicast=yes
       resources: ioport:d800-d8ff iomemory:fddfc000-fddfc0ff irq:18

---

### Post by noob12 on 2007-08-12
> 
sorry if this may sound stupid, but how can I tell what the speed of my switch is?
and what are pre-up lines?


If you don't know, it's probably a 10/100 switch.  Most these days are.  To be sure, you should look at the specific model and version number on the switch and if the switch doesn't actually say on it, then look up the specs on the vendor's site.

For the definition of **pre-up** lines read the output of **man interfaces**.  Basically you can set arbitrary commands in your /etc/network/interfaces file to run just before an interface comes up.  An example of such a line is the **ethtool** command I indicated; you can use a pre-up command like that if you have trouble getting it to autonegotiate, but it runs fine once you have done that.  If it autonegotiates properly on its own, leave it alone.  This is meant as a workaround, not an improvement in the normal case.

For example:
```

auto eth3
iface eth3 inet dhcp
pre-up /usr/sbin/ethtool -s eth3 speed 100 duplex full autoneg off

```

Earlier, when you showed me, your card had negotiated to 10mbps.  If your switch handles 100, you can safely do the above to avoid it mistakenly negotiating 10.

---

