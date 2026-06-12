---
title: "Lenovo G50-80 Ubuntu 14.04 Wifi not working."
date: 2015-10-05
forum: Networking &amp; Wireless
---

### Post by alejandro37 on 2015-10-05
Hi!

I've bought a Lenovo G50-80, and I've installed Ubuntu 14. I have a problem with Wifi, because it only works for few minutes, when in Windows 8 it works. I've read several threads about it, but I have not been able to solve it. I've reinstalled Ubuntu 14, but the problem persists.


Thanks and sorry for my English.

---

### Post by alejandro37 on 2015-10-06
The solutions is:

Run in terminal


sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "options iwlwifi 11n_disable=1"
and reboot.


This will disable 802.11n mode, that works badly with many Intel wireless adapters.

(Solution by Pilot6)

---

### Post by Bucky Ball on 2015-10-06
And open a terminal and give the output of this between code tags (see the last link in my signature):

```
sudo lshw -C network
```

---

### Post by jeremy31 on 2015-10-06
I would be interested in seeing if ```
[COLOR=#000000]sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "options iwlwifi 11n_disable=8"
```

works and allows full 11N functionality

[/COLOR]

---

### Post by alejandro37 on 2015-10-07
The output of command "[COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C network[/FONT][/COLOR]" is:
```
*-network                      description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 68:f7:28:e1:0f:8b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:4000(size=256) memory:d1204000-d1204fff memory:d1200000-d1203fff
  *-network
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 93
       serial: 34:e6:ad:c4:c3:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-30-generic firmware=25.17.12.0 ip=192.168.1.130 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:50 memory:d1100000-d1101fff
```

Hi jeremy31!

Do you want me to try with [COLOR=#000000][FONT=Ubuntu Mono]sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "options iwlwifi 11n_disable=8" instead of [/FONT][/COLOR][COLOR=#000000]sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "options iwlwifi 11n_disable=1"[/COLOR]?

Thanks!

---

### Post by jeremy31 on 2015-10-07
I would like you to try it, if it doesn't work use Pilot6's command and reboot

---

### Post by alejandro37 on 2015-10-07
Ok, I've tried with your command, and until now it works fine!

---

### Post by Bucky Ball on 2015-10-07
If it keeps doing so, please see the first link in my signature, thanks. Good luck. :)

---

### Post by alejandro37 on 2015-10-08
I've had a problem with [COLOR=#000000][FONT=Ubuntu Mono]sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "options iwlwifi 11n_disable=8", because wifi didn't work after few minutes, so I had to activate again Pilot6's solution[/FONT][/COLOR]

---

### Post by alejandro37 on 2015-10-27
Good afternoon.


I still having the same problem after a week in which it worked fine, so I don't know what can I do in order to solve it permanently. Can anyone help me? Thanks in advance

---

