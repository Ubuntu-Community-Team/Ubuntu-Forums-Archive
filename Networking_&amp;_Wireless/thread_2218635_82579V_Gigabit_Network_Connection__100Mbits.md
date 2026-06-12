---
title: "82579V Gigabit Network Connection : 100Mbit/s"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by delcenserie on 2014-04-21
Hi, 

I don't arrive to up 1000Mbit/s. Before, i have installed debian 7.4, it run well.
I have download drivers from intel and compile it.
But that the same.

I read any forum but not solution.

root@corsair:/#  lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
root@corsair:/# uname -a
Linux corsair 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
root@corsair:/# 


root@corsair:~# lshw -C network
  *-network               
       description: Ethernet interface
       produit: 82579V Gigabit Network Connection
       fabriquant: Intel Corporation
       identifiant matériel: 19
       information bus: pci@0000:00:19.0
       nom logique: eth0
       version: 06
       numéro de série: 60:a4:4c:e6:a5:9a
       taille: 100Mbit/s
       capacité: 1Gbit/s
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.0.4-NAPI duplex=full firmware=0.13-4 ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       ressources: irq:80 mémoire:fbf00000-fbf1ffff mémoire:fbf28000-fbf28fff portE/S:f040(taille=32)

[   77.091522] e1000e: Intel(R) PRO/1000 Network Driver - 3.0.4-NAPI
[   77.091525] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[   77.091711] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[   77.091731] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[   77.360032] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 60:a4:4c:e6:a5:9a
[   77.360037] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[   77.360074] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[   77.360103] e1000e 0000:0b:00.0: Disabling ASPM L0s L1
[   77.360309] e1000e 0000:0b:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[   77.360340] e1000e 0000:0b:00.0: irq 82 for MSI/MSI-X
[   77.360347] e1000e 0000:0b:00.0: irq 83 for MSI/MSI-X
[   77.360354] e1000e 0000:0b:00.0: irq 84 for MSI/MSI-X
[   77.514081] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[   77.614388] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[   77.614784] e1000e 0000:0b:00.0 eth1: (PCI Express:2.5GT/s:Width x1) 60:a4:4c:e6:a6:90
[   77.614791] e1000e 0000:0b:00.0 eth1: Intel(R) PRO/1000 Network Connection
[   77.614883] e1000e 0000:0b:00.0 eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[   98.309373] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   98.309382] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO

root@corsair:~# ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on (auto)
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes
root@corsair:~# 
root@corsair:~# modinfo e1000e
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        3.0.4-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     B86187D504664D50DF59C36
alias:          pci:v00008086d000015A3sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A2sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A1sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001559sv*sd*bc*sc*i*
alias:          pci:v00008086d0000155Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:        
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)
parm:           EEE:Enable/disable on parts that support the feature (array of int)
parm:           Node:[ROUTING] Node to allocate memory on, default -1 (array of int)
parm:           debug:Debug level (0=none,...,16=all) (int)
root@corsair:~# 

Thanks for your help

---

### Post by delcenserie on 2014-04-21
I find the problem, is the cable.
I tested it with debian. and have the same. When i moved the cable, i see 1000Mbits.

Now, it's ok.

tof@corsair:~$ dmesg |grep e1000e
[    1.149639] e1000e: module verification failed: signature and/or  required key missing - tainting kernel
[    1.151054] e1000e: Intel(R) PRO/1000 Network Driver - 3.0.4.1-NAPI
[    1.151057] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    1.151250] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.151268] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[    1.414237] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 60:a4:4c:e6:a5:9a
[    1.414239] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.414272] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.414290] e1000e 0000:0b:00.0: Disabling ASPM L0s L1
[    1.414462] e1000e 0000:0b:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.414481] e1000e 0000:0b:00.0: irq 82 for MSI/MSI-X
[    1.414484] e1000e 0000:0b:00.0: irq 83 for MSI/MSI-X
[    1.414487] e1000e 0000:0b:00.0: irq 84 for MSI/MSI-X
[    1.539811] e1000e 0000:0b:00.0 eth1: (PCI Express:2.5GT/s:Width x1) 60:a4:4c:e6:a6:90
[    1.539813] e1000e 0000:0b:00.0 eth1: Intel(R) PRO/1000 Network Connection
[    1.539901] e1000e 0000:0b:00.0 eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    4.717731] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[    4.820653] e1000e 0000:00:19.0: irq 80 for MSI/MSI-X
[    7.541710] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
tof@corsair:~$ ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on (auto)
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes
tof@corsair:~$

---

### Post by mörgæs on 2014-04-21
Good, if this solves your problem please mark the thread so.

---

