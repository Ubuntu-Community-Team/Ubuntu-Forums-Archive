---
title: "Wireless speed issues with Realtek rtl8821ae"
date: 2014-12-20
forum: Networking &amp; Wireless
---

### Post by dfriedberg on 2014-12-20
I just purchased my computer and have been using the wireless successfully but the connection is very slow. My install of ubuntu was fine with no errors. This machine only runs Ubuntu no other OSs are on it. I'm a new to Linux so I will need a detailed answer advice.

In active network connections it shows:
[IMG]http://www.davidfriedberg.com/wireless.jpg[/IMG]

**System Information:**
Gigabyte Brix Pro i5
16GB RAM
Sandisk Ultra II SSD
Ubuntu 14.10 

According to my Connection information my speed is 6Mb/s for bursts it will go up to 110Mb/s it shows no driver information. 

According to my router I have a 80% signal strength and on a 52Mbps connection on the Ubuntu machine. My windows machine using wireless N sitting next to this machine only has a 78% signal but a 144Mb/s connection and  my iPhone using AC is getting 242Mb/s. 

Is there a driver for this card? I'm open to buying a different mini pci wireless card which is the fastest best supported card with Ubuntu?

My router is a Netgear NIghthawk AC1900.

Thank you.


This is the output for **lsusb**:
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 13d3:3414 IMC Networks 
Bus 003 Device 003: ID 04d9:0132 Holtek Semiconductor, Inc. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


This is the output from **lshw**:

```

  *-network               
       description: Wireless interface
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 54:27:1e:65:89:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=3.16.0-28-generic firmware=N/A ip=192.168.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 ioport:e000(size=256) memory:f7d00000-f7d03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 0c
       serial: 74:d4:35:c6:0f:91
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:d000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff



```

---

### Post by dfriedberg on 2014-12-20
[B]I did some research and just bought this card:
[/B][http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth.html](http://www.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7260-bluetooth.html)

I was able to get it for free with Amazon points money. This has Linux drivers and I believe they are built in by default to Ubuntu. There where some complaints about Bluetooth performance but I don't use Bluetooth anyway.

---

