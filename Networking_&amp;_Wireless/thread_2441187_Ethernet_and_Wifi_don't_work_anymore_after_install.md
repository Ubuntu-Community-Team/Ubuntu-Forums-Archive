---
title: "Ethernet and Wifi don't work anymore after installing new Linux header"
date: 2020-04-20
forum: Networking &amp; Wireless
---

### Post by dhiaagr on 2020-04-20
Hi all;
After installing ```
Linux 5.0.0-37-generic #40~18.04.1-Ubuntu SMP Thu Nov 14 12:06:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

My Ethernet and Wifi cards don't show up in ```
ip link[CODE] anymore.

Here's some additional information :
[FONT=courier new]
**$ ip link**[/FONT]
[CODE]
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
```

[FONT=courier new]**$ lspci -nn | grep et**[/FONT]
```
 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15) 
03:00.0 Network controller [0280]: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] [8086:24fb] (rev 10)
```

**[FONT=courier new]$ sudo lshw -C network[/FONT]**
```

  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0304000-f0304fff memory:f0300000-f0303fff
  *-network UNCLAIMED
       description: Network controller
       product: Dual Band Wireless-AC 3168NGW [Stone Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f1000000-f1001fff

```

Any help would be appreciated, thank you ( :

---

### Post by dhiaagr on 2020-04-20
So, since the problem was related to me installing a new version of the Linux header without thinking, I managed to revert back to the older linux image.

```
$sudo nano /boot/grub/grub.conf
```
search for <new linux image>
replace with <desired linux image>
Save and reboot.
Everything seems working fine and I'm back to step 0 in which ethernet works fine but not the Wifi.

---

### Post by slickymaster on 2020-04-20
*Thread moved to **Networking & Wireless**.*

---

