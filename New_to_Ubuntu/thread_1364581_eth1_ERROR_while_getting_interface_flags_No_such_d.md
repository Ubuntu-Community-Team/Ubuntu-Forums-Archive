---
title: "eth1: ERROR while getting interface flags: No such device"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by nateman7097 on 2009-12-26
Tried to install and configure aircrack, and  upon  restarting my  computer, I cannot  use  my wireless connection. I  tried right clicking the network connection icon,  but there is no  option to  enable wireless.

This  might help explain the  situation.

nathan@nathan-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: BLOCKED
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:25 memory:b4000000-b4003fff ioport:3000(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=24 mingnt=3
       resources: memory:b8006000-b8006fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: BLOCKED
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

I  tried  searching the forums, and  I  could not find anyone with a similar  problem.  

Does anyone know how I can  enable my eth1 wireless  connection?

---

### Post by Iowan on 2009-12-26
Check */etc/network/interfaces* to see if a definition for eth1 might have gotten put there. That'd derail NM controlling it (but shouldn't generate that error).

---

### Post by nateman7097 on 2009-12-26
This is all that is in that file:

auto lo
iface lo inet loopback


:I imagine a lot more needs to be in there.

---

### Post by Iowan on 2009-12-26
In one sense, that's a good thing. Network Manager will ordinarily ignore an interface defined in */etc/network/interfaces*. On the other hand, it might have been a quick fix to simply comment out the definition and reboot.

---

### Post by nateman7097 on 2009-12-26
I think it got modified by accident when I was trying to install aircrack.

---

### Post by nateman7097 on 2009-12-27
Can anyone help me? I still can't get my wireless to work.

---

### Post by nateman7097 on 2009-12-27
I tried just popping in the live CD to see if the default settings for Ubuntu would make the wireless work, and still no luck. 

I also tried changing the /etc/network/interfaces to include eth1, but that did not work. 

I tried playing with the hotkeys, because I am on a laptop, but the wireless light is on, so I don't think the physical card is turned off. 

:confused::confused::confused::confused::confused:

---

### Post by nateman7097 on 2010-01-15
So I bought a wireless network USB adapter, and now that will not pick up any networks. It allows me to check the mark on the enable wireless. I can sit right beside my wireless router and it won't pick it up. I can't even type in the network name and connect.


:evil::evil::evil::evil::evil:

---

