---
title: "wifi driving me nuts, connection keeps dropping, need to reboot to reconnect"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by night116 on 2015-08-16
I have a Ubuntu 15.04
Toshiba Qosmio
Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
800.000 MHz
memory 32349mb
network controller:
intel dual band wireless AC 7260
ethernet contoller: qualcomm atheros AR8161 gigabit ethernet rev10 

And every day and it can happen constantly during the day or night for no reason, the wifi connection just gets dropped, the computer does not try to reconnect, and I usually have to reboot to get the connection back again.
its not the router as I have just purchased another new one an ASUS RT-AC3200 and am using 2.4Ghz, and 2, 5Ghz bands, this has been happening for a few months now.

```
*-network               
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 73
       serial: fc:f8:ae:67:2d:8e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-32-generic firmware=22.24.8.0 ip=192.168.1.18 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:d1000000-d1001fff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth0
       version: 10
       serial: c4:54:44:39:36:ce
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:52 memory:d4500000-d453ffff ioport:3000(size=128)
```

---

### Post by jeremy31 on 2015-08-16
It might help to ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by night116 on 2015-08-17
that didnt work, I also re-installed the latest wifi software from intel, but nothing works at all.

---

