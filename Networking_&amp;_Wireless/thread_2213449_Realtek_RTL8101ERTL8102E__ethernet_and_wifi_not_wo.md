---
title: "Realtek RTL8101E/RTL8102E  ethernet and wifi not working"
date: 2014-03-26
forum: Networking &amp; Wireless
---

### Post by ivan_camilo_barrig on 2014-03-26
Hola,


Actualicé ubuntu de 12.04 a 12.10 y no funciona mi tarjeta de red. No tengo wifi y tampoco reconoce la conexion ethernet.
mi equipo es un hp 1000 y la tarjeta de red es una Realtek RTL8101E/RTL8102E.

despues de ejecutar el comando, lspci :

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Ralink corp. Device 539b
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
 
despues de ejecutar,  rfkill list :

0: phy0: Wireless LAN
                Soft blocked: no
                Hard blocked: no
1: hp-wifi: Wireless LAN
                Soft blocked: no
                Hard blocked: no

por ultimo ejecuté,  sudo lshw -c network:

sudo] password for ivancamilobarriga: 
  *-network DESACTIVADO   
       descripción: Interfaz inalámbrica
       producto: Ralink corp.
       fabricante: Ralink corp.
       id físico: 0
       información del bus: pci@0000:01:00.0
       nombre lógico: wlan0
       versión: 00
       serie: 1c:3e:84:69:d7:5c
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=rt2800pci driverversion=3.5.0-42-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       recursos: irq:16 memoria:52500000-5250ffff
  *-network DESACTIVADO
       descripción: Ethernet interface
       producto: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:08:00.0
       nombre lógico: eth0
       versión: 05
       serie: 2c:59:e5:a4:59:38
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100Mbit/s
       recursos: irq:42 ioport:2000(size=256) memoria:52404000-52404fff memoria:52400000-52403fff



Estas son las herramientas que conozco, agradezco su colaboracion.

---

