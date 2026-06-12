---
title: "TP Link N900 PCIe Wireless card not connecting Ubuntu 16.04"
date: 2016-08-21
forum: Networking &amp; Wireless
---

### Post by abefroman99 on 2016-08-21
TP Link N900 PCIe Wireless card not connecting (according to the reviews its compatible) on Ubuntu 16.04 (new install).

```
$ lspci |grep Ath
02:00.0 Ethernet controller: Qualcomm Atheros Device abcd (rev 01)

$ sudo modprobe -vv ath9k
modprobe: INFO: ../libkmod/libkmod.c:364 kmod_set_log_fn() custom logging function 0x55ba5f25a4a0 registered
modprobe: INFO: ../libkmod/libkmod.c:331 kmod_unref() context 0x55ba608251e0 released

$ sudo lsmod |grep -i ath
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211

$ nmcli c
NAME                UUID                                  TYPE            DEVICE 
Wired connection 1  c10d5885-6d4a-46b4-b927-5f4680874610  802-3-ethernet  enp4s0 

$ sudo lshw -C network 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f3200000-f321ffff memory:f3220000-f322ffff

$ sudo modinfo ath9k |grep -v alias
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     323EDC06388A3D0920FD7FC
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
```

Here is my on board eth:
```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
```

When I click on the arrow to manage networking it only shows the wired ethernet connection and nothing about wireless.

I tried a number of other steps but to no avail.

```
$ sudo apt-get install atheros-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package atheros-firmware
```

I'm trying to install the atheros firmware, but its not found, even though I have everything checked in the software center.

What else should I try/check?

---

### Post by jeremy31 on 2016-08-21
Please post the result of ```
lspci -nnk | grep -iA2 net
```

Please use code tags when posting terminal output, see the link in my signature for one method.  With advanced reply use the # symbol that appears in the second row below the title, third from right.

The package atheros-firmware is a Debian package and most atheros firmware in Ubuntu is part of linux-firmware which is installed by default

---

### Post by chili555 on 2016-08-21
I'll bet your Atheros isn't an ath9k device. Also, ath9k doesn't need firmware:```
chili@T440p:~$ modinfo ath9k
filename:       /lib/modules/4.4.6-040406-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F7E3AF932B15681132EA595
[COLOR="#FF0000"]firmware ???[/COLOR]
```Let's see what your device *really *is:```
lspci -nn | grep 0280
```Man! Jeremy is kwik!!

---

### Post by abefroman99 on 2016-08-21
Here's the output:
```
$ sudo lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:abcd] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:859e]
	Kernel driver in use: r8169
	Kernel modules: r8169

```

```
$ sudo lspci -nn | grep 02
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 04)
02:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:abcd] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)

```

---

### Post by chili555 on 2016-08-21
> I figured out that the problem is with the BIOS on the motherboard of the host 
device. Some BIOS do not fully read the EPROM contents on the Sparklan radio. I 
have used the Sparklan PCIe express card on the same embedded baseboard with 
Intel Atom Q7 modules and it seems to be properly recognized by one and not the 
other from a different manufacturer. The BIOS was on the Q7 modules and not the 
baseboard so each module had a different BIOS.From: [https://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg07514.html](https://www.mail-archive.com/ath9k-devel@lists.ath9k.org/msg07514.html)> ID abcd is used by Atheros devices when not properly initialized by BIOS.From: [https://pci-ids.ucw.cz/read/PC/168c/abcd](https://pci-ids.ucw.cz/read/PC/168c/abcd)

Will you please check that the device is seated correctly? Perhaps try another PCI slot? And please check the BIOS to see that the device is enabled.

---

### Post by abefroman99 on 2016-08-21
```
06:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)
	Subsystem: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:3112]
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

Thanks!  I tried a different PCIe port, and set something in the bios to auto (it was disabled) and its working now.

---

### Post by chili555 on 2016-08-21
Awesome! Glad it's working! Please use thread tools at the top to mark Solved.

---

