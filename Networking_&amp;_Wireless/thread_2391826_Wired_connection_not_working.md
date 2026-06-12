---
title: "Wired connection not working"
date: 2018-05-13
forum: Networking &amp; Wireless
---

### Post by goldenp on 2018-05-13
Hi
 
I just installed Ubuntu on an Asus machine, dual boot with preinstalled windows 10 using a liveUSB key.
Wifi seems to be working ok, but wired doesn’t, while it works fine on Windows.
The wired connection seems to be ‘connecting’ but then i get an error message saying that activating the connection failed.
 
I tried sudo apt update and sudo apt dist-upgrade, reboot but this changed nothing.
 
 
 
Output of sudo lshw -C network
  ```
*-network                
       description: Ethernet interface
       produit: Ethernet Connection I217-V
       fabriquant: Intel Corporation
       identifiant matériel: 19
       information bus: pci@0000:00:19.0
       nom logique: eno1
       version: 05
       numéro de série: 10:c3:7b:96:df:66
       taille: 1Gbit/s
       capacité: 1Gbit/s
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       ressources: irq:25 mémoire:f7200000-f721ffff mémoire:f7239000-f7239fff portE/S:f040(taille=32)
  *-network
       description: Interface réseau sans fil
       produit: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: wlp3s0
       version: 00
       numéro de série: 54:27:1e:e7:18:f9
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-20-generic firmware=N/A ip=172.20.10.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       ressources: irq:30 portE/S:d000(taille=256) mémoire:f7100000-f7103fff
```
 
Output of sudo ethtool eno1
```
Settings for eno1:
            Supported ports: [ TP ]
            Supported link modes:   10baseT/Half 10baseT/Full
                                    100baseT/Half 100baseT/Full
                                    1000baseT/Full
            Supported pause frame use: No
            Supports auto-negotiation: Yes
            Supported FEC modes: Not reported
            Advertised link modes:  10baseT/Half 10baseT/Full
                                    100baseT/Half 100baseT/Full
                                    1000baseT/Full
            Advertised pause frame use: No
            Advertised auto-negotiation: Yes
            Advertised FEC modes: Not reported
            Speed: 1000Mb/s
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
```

---

