---
title: "wireless card troubles"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by lacitpo on 2008-06-27
I'm having trouble with my wireless card.  It's a Broadcom BCM4318 [AirForce One 54g].  Ubuntu seems to be recognizing that I have a wireless card but from what I can tell it may be messing something up.  This is a laptop with a built in wireless card.  when I click on the network stuff on my top panel, it seems like it cannot find any wireless networks in range though there is one.

When I run lshw I recieve this information

```
*-network:0

description : Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless Lan Controller
vendor: Broadcom Corperation
physical id: 2
bus info: pci@0000:06:02:0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency= 64 module=ssb
```

However, I also have this info lower down

```
*-network

description: Wireless  interface
physcial id: 1
logical name: wlan0
serial: 00:14:a5:6c:89:be
capabiliteis: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

So best I can tell maybe there is some problem with the real card not having a logical name in the system.  Again, I don't know a lot about this, but when I've run this command, 

sudo -lshw -businfo -c network, I get this 

```
pci@0000:06:02.0          network    BCM4318 [Airforce Once 54g] 802.11g W
pci@0000:06:06.0  eth0    network    RTL-8139/8139C/8139C+
                  wlan0   network    Wireless interface
```

which seems to back up my suspicion.  The driver being used is FWcutter.  Would be greatful to anyone who can help.

---

