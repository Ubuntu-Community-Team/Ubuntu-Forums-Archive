---
title: "Wireless issues on  mini PC ASUS e520"
date: 2022-12-03
forum: Networking &amp; Wireless
---

### Post by pierragol60 on 2022-12-03
Hello community,
I've install ubuntu 20.04 LTS on a mini PC ASUS e520.
Wireless hardare doesn't work.

I'm newbee in ubuntu and I tried : ~/Bureau$ sudo lshw -C network
  *-network NON-RÉCLAMÉ     
       description: Network controller
       produit: Wireless 8265 / 8275
       fabricant: Intel Corporation
       identifiant matériel: 0
       information bus: pci@0000:02:00.0
       version: 78
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress cap_list
       configuration : latency=0
       ressources : mémoire:f7100000-f7101fff
  *-network
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: enp3s0
       version: 15
       numéro de série: b0:6e:bf:1e:4a:94
       taille: 1Gbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration : autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-56-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.0.0.17 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       ressources : irq:17 portE/S:e000(taille=256) mémoire:f7004000-f7004fff mémoire:f7000000-f7003fff

Any idea how to fix this issue.

Pierre,

---

### Post by chili555 on 2022-12-03
Please run and post the result of:

```
sudo modprobe iwlwifi
sudo dmesg | grep iwl
```

---

