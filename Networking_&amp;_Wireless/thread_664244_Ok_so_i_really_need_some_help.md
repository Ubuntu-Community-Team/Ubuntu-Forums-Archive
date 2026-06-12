---
title: "Ok so i really need some help"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by tampabuc2004 on 2008-01-11
So i finally ogt my wireless card to work or at least i thought i did and i go to connect to a network fill in all the info and then it says it is connected but i cant see ne other computers and i cant connect to the internet. now i followed this how to and it still doesnt work [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)


 now here is some info
wulfy@wulfy-laptop:~$ sudo lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) 
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01) 
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) 
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

wulfy@wulfy-laptop:~$ sudo lshw -C network 
  *-network:0             
       description: Ethernet interface 
       product: BCM4401 100Base-T 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       logical name: eth0 
       version: 01 
       serial: 00:c0:9f:66:36:0d 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s 
  *-network:1 
       description: Wireless interface 
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) 
       vendor: Linksys, A Division of Cisco Systems 
       physical id: 4 
       bus info: pci@0000:02:04.0 
       logical name: wlan0 
       version: 00 
       serial: 00:0e:9b:68:ec:a3 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.51+LanExpress,08/11/2004,2.22. ip=192.168.10.5 latency=64 link=yes maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by tampabuc2004 on 2008-01-11
Ok nevermind i got it working now and all is good

---

