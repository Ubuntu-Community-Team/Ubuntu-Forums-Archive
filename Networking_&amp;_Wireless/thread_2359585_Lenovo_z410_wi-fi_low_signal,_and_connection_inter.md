---
title: "Lenovo z410 wi-fi low signal, and connection interrupted."
date: 2017-04-25
forum: Networking &amp; Wireless
---

### Post by haly88 on 2017-04-25
Hi to all,
I'm been using Ubuntu (16.04 right now) in my notebook Lenovo ideapad Z410 for almost tree years now,
I want to share with you some wi-fi issue i'm having since the beginning.


I'm able to connect to any wi-fi network, but with a really low signal, and it always trying to reconnect to the same network i'm already in.
If i'm really close to the router, the wi-fi works better, but if i step a few meters away, this issues will begin.
Wi-fi is working fine on other devises and computers.


I have read and try some solutions, but i'm really not an expert.
It seams to be some issue with bcmwl-kernel-source driver,

I read this post and try some "null pointer fix" without success (maybe i'm doing it wrong) 
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1379524](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1379524)

Card: (Broadcom BCM43142 802.11b/g/n) (notebook internal WiFi card).
Here is my hardware info (sudo lshw -C network) 

```

*-network               
       descripción: Ethernet interface
       producto: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:08:00.0
       nombre lógico: eth0
       versión: 07
       serie: 28:d2:44:6c:73:a4
       tamaño: 10Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:29 ioport:3000(size=256) memoria:b5600000-b5600fff memoria:b5400000-b5403fff
  *-network
       descripción: Interfaz inalámbrica
       producto: BCM43142 802.11b/g/n
       fabricante: Broadcom Corporation
       id físico: 0
       información del bus: pci@0000:09:00.0
       nombre lógico: wlan0
       versión: 01
       serie: 14:2d:27:fb:ea:0d
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.1.83 latency=0 multicast=yes wireless=IEEE 802.11abg
       recursos: irq:16 memoria:b5500000-b5507fff
  *-network DESACTIVADO
       descripción: Ethernet interface
       id físico: 3
       nombre lógico: virbr0-nic
       serie: 52:54:00:4c:82:56
       tamaño: 10Mbit/s
       capacidades: ethernet physical
       configuración: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s

```

Any help will be appreciated, thanks.

---

