---
title: "Intel WiFi 6 AX200 not working on 22.04 LTS"
date: 2022-09-20
forum: Networking &amp; Wireless
---

### Post by sbansal1999 on 2022-09-20
I am currently on Ubuntu 22.04 LTS and Intel WiFi 6 AX200 is installed on my laptop. Many a times the WiFi Settings Panel says unavailable and also says "No Wi-Fi Adapter Found". Sometimes the WiFi appears by itself and now its gone. I have installed the latest drivers from [https://www.intel.in/content/www/in/en/support/articles/000005511/wireless.html](https://www.intel.in/content/www/in/en/support/articles/000005511/wireless.html) 
I searched on some forums on what to do but nothing worked. I ran ```
sudo lshw -C network
``` and it gave the following output:
```
sudo lshw -C network                 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 16
       serial: f8:0d:ac:07:f6:6a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-47-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:52 ioport:e000(size=256) memory:fca04000-fca04fff memory:fca00000-fca03fff
  *-network DISABLED
       description: Wireless interface
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlo1
       version: 1a
       serial: ac:12:03:41:41:28
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.15.0-47-generic firmware=66.f1c864e0.0 cc-a0-66.ucode ip=10.53.20.229 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:78 memory:fc900000-fc903fff
  *-network
       description: Ethernet interface
       physical id: a
       bus info: usb@1:2
       logical name: usb0
       serial: aa:5f:6b:92:ae:b4
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=rndis_host driverversion=5.15.0-47-generic duplex=half firmware=RNDIS device ip=192.168.109.104 link=yes multicast=yes port=twisted pair

```
Currently I am using internet by USB Tethering from my mobile device. I am Dual Boot with Windows 11 the WiFi behaves the same way on that as well. 
I have tried disabling Fast Boot on Windows but still the issue persists.

---

### Post by chili555 on 2022-09-20
> I am Dual Boot with Windows 11 the WiFi behaves the same way on that as well.That strongly suggests a hardware issue, not a driver or operating system issue.

---

### Post by Yellow Pasque on 2022-09-22
Yes, it sounds like it could be a loose connection or a flaky wifi chip. What model laptop?

---

