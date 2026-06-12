---
title: "Wired ethernet not working, but wireless works fine after upgrade to 18.04"
date: 2018-09-28
forum: Networking &amp; Wireless
---

### Post by fsx.comp on 2018-09-28
Hi,
Recently upgraded Ubuntu from 16.04 to 18.04 and now wired ethernet is not working at all, but wireless works fine (through USB Wi-Fi dongle). Before upgrade wired sometimes worked sometimes not. I have dual boot so when booted to Windows wired ethernet always works fine. I'm using buit-in network card on ASUS GRYPHON Z87 motherboard.
Below is result of "sudo lshw -C network":
```

  *-network                 
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 74:d0:2b:2c:03:61
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:26 memory:f7c00000-f7c1ffff memory:f7c3c000-f7c3cfff ioport:f080(size=32)
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:3
       logical name: wlx801f02e01e4d
       serial: 80:1f:02:e0:1e:4d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.15.0-34-generic firmware=0.36 ip=192.168.1.69 link=yes multicast=yes wireless=IEEE 802.11

```

Also I have tried to run Ubuntu 18.04 Live USB and wired connection hasn't worked there, too.
Thanks for advice.

---

