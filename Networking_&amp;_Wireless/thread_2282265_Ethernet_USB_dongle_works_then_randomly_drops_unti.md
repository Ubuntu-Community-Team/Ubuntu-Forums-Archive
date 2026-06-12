---
title: "Ethernet USB dongle works then randomly drops until restart"
date: 2015-06-13
forum: Networking &amp; Wireless
---

### Post by el_garicimo on 2015-06-13
Hey all,

I've been using xubuntu 14.04 as my daily driver for a while now, as I've been getting into web development. I'm using a dell ultrabook that has no ethernet port (XPS 12 9Q33), and so I have usb 2.0 ethernet dongle.

The dongle will work fine for a couple hours and then randomly stop working. Unplugging and repluggin the dongle does not even register any lights on the dongle, it's like it's dead. If I restart the computer, things seem to work again.

 When I type dmesg, the error code I get is `asix 2-2:1.0 (unregistered net_device): Failed to enable hardware MII access`

After some searching around, I don't see any clear troubleshooting path...any ideas?

---

### Post by Bucky Ball on 2015-06-13
*Thread moved to **Networking & Wireless**.*

Ethernet dongle? You have an ethernet cable plugged in to it? I've never heard of such a thing and would be curious to see one. 

Do you mean wireless USB dongle? :-k

With the dongle plugged in please issue this command:

```
sudo lshw -C network
```

Post the output back here, please, between code tags (last link in my signature).

---

### Post by el_garicimo on 2015-06-13
By ethernet dongle I mean something like this: [http://ecx.images-amazon.com/images/I/41Uqzy7OL6L._SY300_.jpg](http://ecx.images-amazon.com/images/I/41Uqzy7OL6L._SY300_.jpg)

Female cat-45 jack on one end, male usb on the other.

It's actually working right now, so I'll post the troubleshooting output when it decides to crap out...the working output is here:
```

*-network DISABLED      
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 6b
       serial: 5c:51:4f:11:6f:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-54-generic firmware=22.24.8.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:62 memory:f7c00000-f7c01fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: 00:00:00:00:00:01
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Dec-2011 duplex=full firmware=ASIX AX88772B USB 2.0 Ethernet ip=192.168.2.185 link=yes multicast=yes port=MII speed=100Mbit/s

```

---

### Post by el_garicimo on 2015-06-13
Ok, it decided to crap out...below is the output of sudo lshw -C network:

```

 *-network DISABLED      
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 6b
       serial: 5c:51:4f:11:6f:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-54-generic firmware=22.24.8.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:62 memory:f7c00000-f7c01fff

```

---

