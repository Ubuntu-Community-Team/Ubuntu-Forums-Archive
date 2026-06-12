---
title: "Problem with wifi - intermittent conexion"
date: 2014-04-16
forum: Networking &amp; Wireless
---

### Post by flopezlira on 2014-04-16
Please help. Mi wifi connects intermittently. Is a big problem because I take courses online. Any help will be appreciated.

 sudo lshw -C network
  *-network               
       descripción: Interfaz inalámbrica
       producto: RTL8723AE PCIe Wireless Network Adapter
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: wlan0
       versión: 00
       serie: a4:db:30:67:91:4e
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=rtl8723ae driverversion=3.8.0-39-generic firmware=N/A ip=192.168.1.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       recursos: irq:18 ioport:e000(size=256) memoria:f7c00000-f7c03fff
  *-network
       descripción: Ethernet interface
       producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0.2
       información del bus: pci@0000:03:00.2
       nombre lógico: eth0
       versión: 0a
       serie: 00:90:f5:f0:95:f2
       tamaño: 10Mbit/s
       capacidad: 1Gbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:43 ioport:d000(size=256) memoria:f0a04000-f0a04fff memoria:f0a00000-f0a03fff
francisco@francisco-W5x0EU1:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"MOVISTAR_BE38"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: F8:1B:FA:5A:BE:41   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:475   Missed beacon:0

---

### Post by flopezlira on 2014-04-16
Searching in the forum, maybe my problem is that the wifi connection is slow rather than working [COLOR=#000000]intermittently[/COLOR]

---

