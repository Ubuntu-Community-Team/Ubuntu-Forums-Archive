---
title: "Problem with wireless card 16.04"
date: 2017-10-03
forum: Networking &amp; Wireless
---

### Post by egr095 on 2017-10-03
So, i just bought a new laptop (HP 15 bs-013ns), and installed Ubuntu 16.04 alongside Windows 10. Up to the point where I finished installing Ubuntu everything was fine, I can dual-boot without a problem... But then I realized my wireless card was not working, or at least wireless networks weren't being listed by Network Manager. Tried restarting the service but no luck.

So I run lshw -C network:

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 15
       serial: f4:30:b9:d8:4e:60
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:127 ioport:4000(size=256) memory:b1104000-b1104fff memory:b1100000-b1103fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:b1000000-b100ffff

 lspci -nnk | grep -A2 0280:
   03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    DeviceName: Hanksville Gbe Lan Connection
    Subsystem: Hewlett-Packard Company Device [103c:8319]

rfkill list all:
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

It seems like a driver related problem. Secure Boot is disabled, by the way. I've done some research and I'm afraid this device may not be supported yet.
Still, I'm a bit lost here to be honest, so I'm asking for help here as a last resort.
Thanks in advance.

---

### Post by r102 on 2017-10-03
Do you have possibility to check if the internet works with a wired connection?

---

### Post by egr095 on 2017-10-03
Yes, it does

---

### Post by ajgreeny on 2017-10-03
See **Wireless-info** in my signature below and run the script then post back here the output you get from that.

If the output is too large to post use ubuntu [pastebin]("http://pastebin.ubuntu.com/") instead and give us the link to that page.

---

### Post by egr095 on 2017-10-03
[http://pastebin.ubuntu.com/25669717/](http://pastebin.ubuntu.com/25669717/)

---

### Post by jeremy31 on 2017-10-03
That wireless card is not supported in Linux yet.  Larry Finger is still waiting for the source code from the manufacturer
[https://github.com/lwfinger/rtlwifi_new/issues/267](https://github.com/lwfinger/rtlwifi_new/issues/267)

---

