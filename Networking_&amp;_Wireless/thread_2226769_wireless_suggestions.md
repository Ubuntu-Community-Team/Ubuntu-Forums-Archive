---
title: "wireless suggestions"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by Michaelocalypse on 2014-05-28
I'm not exactly sure what my computer has.  All I can find on specs is: 2 x Realtek GbE LAN chips (10/100/1000 Mbit)

I'd like to get a wireless adapter so I can move my computer to another room.  The signal isn't great there and people have told me to get a repeater.  I'm new to the repeater stuff, but I've but USB adapters in other (windows) computers.  Any suggestions as to what I should go with?  Or does it not matter all that much?

---

### Post by Bucky Ball on 2014-05-29
Please open a terminal and post the output of this command:

```
sudo lshw -C network
```

Thanks.

---

### Post by Michaelocalypse on 2014-05-31
Here's the useful info it gave:
> 
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., LTD.
size: 10Mbits/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz

---

### Post by Bucky Ball on 2014-06-01
All of the output, please. ;)

---

### Post by Michaelocalypse on 2014-06-03
Oh, ok.  For some reason I couldn't get it to copy/paste last time, got a little lazy with typing it all out.

> 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: 06
       serial: 94:de:80:60:1c:ad
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth3
       version: 06
       serial: 94:de:80:61:4f:fc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.0.7 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff




---

### Post by gordintoronto on 2014-06-04
Your computer has two Ethernet ports, which doesn't move you forward for wireless.

Some wireless adapters are poorly supported in Linux, or maybe not supported at all. I have found that my TP-Link TL-WN722N "just works" with 12.04 or later. Avoid getting something which was released last week, because it might not be supported yet.

---

### Post by Michaelocalypse on 2014-06-05
Yeah, I guess I could've mentioned it only has two ethernet ports and I was looking for a USB or something.  I've used them on other computers.

Thanks for the suggestion.  I have 12.04.  What exactly do you mean by "just works"?

---

### Post by gordintoronto on 2014-06-05
'What exactly do you mean by "just works"?'

I plug in the USB, boot up the computer, the Wi-Fi works. You still have to identify what SSID you want to connect to, and the passphrase, but the hardware and driver require no effort at all.

---

### Post by Michaelocalypse on 2014-06-06
Gotcha.  Doesn't seem to cost much and it comes with a free base to get it some distance from the computer on Newegg.  Might help with reception given where I have to move the computer to.

---

### Post by Michaelocalypse on 2014-06-13
It didn't come with a free base for some reason, but worked well.  Didn't have to run the installation CD.  I guess it'll work well enough.  I won't bother with a repeater for now.

Thanks!

---

