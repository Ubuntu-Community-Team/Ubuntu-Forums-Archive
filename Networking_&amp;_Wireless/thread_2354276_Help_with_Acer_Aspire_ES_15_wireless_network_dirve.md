---
title: "Help with Acer Aspire ES 15 wireless network dirvers"
date: 2017-03-01
forum: Networking &amp; Wireless
---

### Post by jberdugo on 2017-03-01
After installing ubuntu 16.04 on a Acer Aspire ES 15 (dual boot with windows 10, Secure Boot disabled) the wireless network card has not worked, it doesn't show up.


I've run thw wireless info script with the following results: [http://paste.ubuntu.com/24090300/](http://paste.ubuntu.com/24090300/)

I've run into posts like this one [http://askubuntu.com/questions/761917/wifi-is-not-working-on-an-acer-aspire-e-15-ubuntu-16-04-kernel-4-4-0-21-gener](http://askubuntu.com/questions/761917/wifi-is-not-working-on-an-acer-aspire-e-15-ubuntu-16-04-kernel-4-4-0-21-gener) but their problem is they had installed backports, but I haven't tried anything. The `modinfo ath10k_pci` shows: 

```

filename:       /lib/modules/4.4.0-63-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
alias:          pci:v0000168Cd00000042sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000040sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000041sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-63-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

```

sudo lshw -c network:

```

  *-network               
       descripción: Ethernet interface
       producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:01:00.0
       nombre lógico: enp1s0
       versión: 15
       serie: 1c:39:47:f5:94:f2
       tamaño: 10Mbit/s
       capacidad: 1Gbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:276 ioport:3000(size=256) memoria:b1104000-b1104fff memoria:b1100000-b1103fff
  *-network NO RECLAMADO
       descripción: Network controller
       producto: Intel Corporation
       fabricante: Intel Corporation
       id físico: 0
       información del bus: pci@0000:02:00.0
       versión: 10
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress cap_list
       configuración: latency=0
       recursos: memoria:b1000000-b1001fff



```

---

### Post by jeremy31 on 2017-03-01
You need the 4.8 kernel
```
sudo apt-get update && sudo apt-get install linux-generic-hwe-16.04
```
Reboot

---

### Post by jberdugo on 2017-03-01
Yes, that solved the problem, thanks a lot jeremy31.


Just took a look back at the askubuntu post and noticed... were you really the same user who answered that question?

---

### Post by jeremy31 on 2017-03-01
Yes
That poster had an Atheros wifi card where you have one of the newer Intel

Please use the thread tools menu near the top of the page to mark as solved

---

