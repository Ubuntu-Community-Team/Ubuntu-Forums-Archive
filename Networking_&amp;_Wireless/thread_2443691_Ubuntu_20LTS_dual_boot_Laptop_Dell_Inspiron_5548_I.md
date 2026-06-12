---
title: "Ubuntu 20LTS dual boot Laptop Dell Inspiron 5548 I can not turn on wifi and in wifi s"
date: 2020-05-19
forum: Networking &amp; Wireless
---

### Post by jss13 on 2020-05-19
hello please ask for your help
  on Laptop Dell Inspiron 5548 I can not turn on wifi and in wifi settings indicates no wifi device was found
  Ubuntu desktop 20 LTS with dual boot
  Inspiron-5548:~$ lspci | grep Wireless 03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
  Inspiron-5548:~$ iwconfig enp2s0 no wireless extensions.
  wlp3s0 IEEE 802.11 ESSID off/any Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm Retry short limit:7 RTS thr: off Fragment thr: off Power Management on
  lo no wireless extensions.
  Inspiron-5548:~$ iwlist Usage: iwlist [interface] scanning [essid NNN] [last] [interface] frequency [interface] channel [interface] bitrate [interface] rate [interface] encryption [interface] keys [interface] power [interface] txpower [interface] retry [interface] ap [interface] accesspoints [interface] peers [interface] event [interface] auth [interface] wpakeys [interface] genie [interface] modulation Inspiron-5548:~$ lspci |grep Network 03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
  Inspiron-5548:~$ lsusb Bus 001 Device 002: ID 8087:8001 Intel Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub Bus 002 Device 003: ID 1bcf:2b8a Sunplus Innovation Technology Inc. Integrated_Webcam_HD Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller Bus 002 Device 004: ID 8087:07dc Intel Corp. Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Inspiron-5548:~$ ip link sho | grep w 3: wlp3s0:  mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
  Inspiron-5548:~$ iwconfig wlp3s0 essid XXXXX key s:XXXXXX Error for wireless request "Set ESSID" (8B1A) : SET failed on device wlp3s0 ; Operation not permitted.
  Inspiron-5548:~$ dhclient wlp3s0 RTNETLINK answers: Operation not permitted
  Inspiron-5548:~$ sudo ifconfig wlp3s0 up [sudo] contraseña para jhzz: Inspiron-5548:
  Inspiron-5548:~$ inxi -MnNs Machine: Type: Portable System: Dell product: Inspiron 5548 v: A10 serial:  Mobo: Dell model: 0FFJC4 v: A00 serial:  UEFI: Dell v: A10 date: 05/28/2019 Network: Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169 IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: 41:12:eb:6f:59:61 Device-2: Intel Wireless 3160 driver: iwlwifi IF: wlp3s0 state: down mac: d0:6e:25:c0:29:92 Sensors: System Temperatures: cpu: 50.0 C mobo: N/A Fan Speeds (RPM): cpu: 2800
  Inspiron-5548:~$ uname -a Linux jz-Inspiron-5548 5.4.0-29-generic #33-Ubuntu SMP Wed Apr 29 14:32:27 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux Inspiron-5548:~$
  root@Inspiron-5548:/home/# lshw -C network *-network descripción: Ethernet interface producto: RTL810xE PCI Express Fast Ethernet controller fabricante: Realtek Semiconductor Co., Ltd. id físico: 0 información del bus: pci@0000:02:00.0 nombre lógico: enp2s0 versión: 07 serie: 34:17:eb:8f:60:63 tamaño: 100Mbit/s capacidad: 100Mbit/s anchura: 64 bits reloj: 33MHz capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation configuración: autonegotiation=on broadcast=yes driver=r8169 duplex=full  firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.0.5 latency=0 link=yes  multicast=yes port=MII speed=100Mbit/s recursos: irq:18 ioport:3000(size=256) memoria:c1200000-c1200fff  memoria:c1000000-c1003fff *-network DESACTIVADO descripción: Interfaz inalámbrica producto: Wireless 3160 fabricante: Intel Corporation id físico: 0 información del bus: pci@0000:03:00.0 nombre lógico: wlp3s0 versión: 83 serie: d0:7e:35:c0:93:29 anchura: 64 bits reloj: 33MHz capacidades: pm msi pciexpress bus_master cap_list ethernet physical  wireless configuración: broadcast=yes driver=iwlwifi  driverversion=5.4.0-29-generic firmware=17.3216344376.0 latency=0  link=no multicast=yes wireless=IEEE 802.11 recursos: irq:50 memoria:c1100000-c1101fff
     :(:confused:

---

### Post by wildmanne39 on 2020-05-19
Thread closed. Please do not post duplicates, it dilutes community effort.

Please use your thread here:

[https://ubuntuforums.org/showthread.php?t=2443689](https://ubuntuforums.org/showthread.php?t=2443689)

---

