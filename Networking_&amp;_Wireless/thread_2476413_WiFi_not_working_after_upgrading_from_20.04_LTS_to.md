---
title: "WiFi not working after upgrading from 20.04 LTS to 22.04 LTS"
date: 2022-06-25
forum: Networking &amp; Wireless
---

### Post by loki-99 on 2022-06-25
Hi,

I've upgraded my Ubuntu 20.04 LTS to 22.04 LTS today and lost WiFi connection on my laptop (Not even showing the WiFi icon).

Below are the outputs for some of the commands related to WiFi card.[B]

lspci | grep -i realtek

[/B]3f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
40:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter (rev ff)

[B]lshw -C network

[/B]  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: enp63s0
       version: 15
       serial: 9c:5a:44:39:df:29
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-40-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:4000(size=256) memory:63204000-63204fff memory:63200000-63203fff



Tired of using internet via cable connection :sad:

---

### Post by mIk3_08 on 2022-06-26
> **loki-99 said:**
> Hi,

I've upgraded my Ubuntu 20.04 LTS to 22.04 LTS today and lost WiFi connection on my laptop (Not even showing the WiFi icon).

Below are the outputs for some of the commands related to WiFi card.[B]

lspci | grep -i realtek

[/B]3f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
40:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter (rev ff)

[B]lshw -C network

[/B]  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: enp63s0
       version: 15
       serial: 9c:5a:44:39:df:29
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-40-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:4000(size=256) memory:63204000-63204fff memory:63200000-63203fff

Tired of using internet via cable connection :sad:
Your WiFi totally vanish... There is no such information about your WiFi device. 
Please run the script below and post the information or pastebin link in this thread. Regards and cheers.
```
https://github.com/UbuntuForums/system-info
```

---

### Post by loki-99 on 2022-06-27
Hi mlk3_08,

Thanks for the reply.

Below is the link of pastebin

[https://paste.ubuntu.com/p/hGw4tdwJF3/](https://paste.ubuntu.com/p/hGw4tdwJF3/)

---

