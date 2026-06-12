---
title: "Network struggles with 8.10"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Wounder on 2008-11-20
While trying to install 8.10 (server) on an old, decrepit box, I've run into a network issue that I can't come to grips with. I've stuck a second NIC in to try to make sure the hardware itself wasn't defunct, but get the same results for both.

At the point the install detects NIC hardware, I get this:
```
eth0: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/1
eth1: 3Com Corporation 3c905C-TX/TX-M [Tornado]

```

Carrying on, with either NIC selected, nets me this:
```
Configuring the network with DHCP - Network autoconfiguration failed
```

Rest of install went swimmingly. From the command line, ifconfig returns lo and nothing else. ping returns the dreaded and expected "Network is unreachable." And at this point, my rarely-used-long-ago-before-three-kids-derailed-career skillz fail me.

Other, possibly relevant info: The box is connected (passing through a switch or two) to a Linksys WRT54G running Tomato 1.19 (which needs updating, I know... three kids, remember!). There are nearly a dozen boxes making use of DHCP with no complaints. Everything else on the network is 5x5.

Help would be sincerely appreciated. I'd offer to name a kid after you, but I'm really, really done having them, regardless of wife's opinion. We could give one of the current batch a new nickname, but that's my final offer. Thanks in advance!

---

### Post by cariboo on 2008-11-20
I'd remove one of the nics and then run:

```
sudo lshw -C network
```

You should get an output similar to this:

```
sudo lshw -c network
[sudo] password for jim: 
  *-network               
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 11
       serial: 00:1b:11:b2:63:65
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.200 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
```

Once you are sure the network card is working, run

```
sudo dhclient eth0
```

and see if you get an ip address.

Jim

---

### Post by Wounder on 2008-11-20
```
sudo lshw -C network
```

returns:

```
*-network DISABLED
```
... along with a bunch of other info that's not particularly relevant until the DISABLED goes away. I'll be googling around for an answer to that now.

Thanks cariboo907!

---

### Post by Wounder on 2008-11-20
```
sudo ifconfig -v eth0 up
```

brings up the NIC and the second command cariboo907 listed nets me an IP as expected. So, well and good. Question now becomes how do I make this happen every time the server boots?

Thanks once again, cariboo907.

---

### Post by Wounder on 2008-11-20
And to hopefully answer my own followup question!

Edit /etc/network/interfaces:
```
sudo vi /etc/network/interfaces
```

Add following lines:
```
# NIC autostart
auto eth0
iface eth0 inet dhcp
```

That seems to have done the trick. If there's a better way, I'd appreciate a followup, seeing as I'm moving on to whatever next disaster awaits me.

---

