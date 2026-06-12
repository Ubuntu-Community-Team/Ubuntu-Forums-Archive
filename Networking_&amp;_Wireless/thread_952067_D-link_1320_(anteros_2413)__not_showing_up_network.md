---
title: "D-link 1320 (anteros 2413)  not showing up network manager"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by cougar618 on 2008-10-18
I bought this D-link card based on the reviews on newegg, which all more or less state that this card works out of the box with ubuntu 8.04. however I cannot get this card to work in ubuntu (or win XP!) dispite trying for hours on in. i also reinstalled ubuntu hoping to solve my issue...

lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3850
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
02:06.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:07.0 Multimedia controller: ATI Technologies Inc Theater 550 PRO PCI [ATI TV Wonder 550]
02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

lshw -C network:
```
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:02:0f.0
       logical name: eth0
       version: 10
       serial: 00:1a:4d:ff:bf:f4
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:3f:51:ff:61
       capabilities: ethernet physical wireless
       conf
```

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"2WIRE144"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1D:5A:1F:03:61   
          Bit Rate=24 Mb/s   
          Encryption key:4858-9550-33   Security mode:open
          Link Quality=42/100  Signal level=32/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
 *****NOTE: eth1 is my usb wifi*****
the restricted drivers show up in sys>adnin>hardware but they don't work.
I think the key to fixing this has to do w/ fixing the 'UNCLAIMED' portion of the lshw -C but i dont know how. i know w/ fedora you could open up network manager and manually create and assign wlan0 or what not, but i can't (or dont know how to) in ubuntu.

thx for help in advance.

---

### Post by cougar618 on 2008-10-18
also 
```

$ dmesg |grep eth0
[   35.977030] eth0: RTL8169sc/8110sc at 0xf882c000, 00:1a:4d:ff:bf:f4, XID 18000000 IRQ 21
[   45.818342] r8169: eth0: link down
[  126.180038] ADDRCONF(NETDEV_UP): eth0: link is not ready
$ dmesg |grep ath
[   40.878756] ath_hal: module license 'Proprietary' taints kernel.
[   40.918692] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   41.163759] ath_pci: 0.9.4


```

is there anything like fedoras's system-network-config?

---

