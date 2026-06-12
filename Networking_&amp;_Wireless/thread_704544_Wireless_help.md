---
title: "Wireless help"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by jaysons on 2008-02-22
Having troubles connecting to my router, here are some details..
Thinkpad R50 - Ubuntu 7.10 - Cisco aironet 350 adapter (air-pcm350) - Wireless ssid = ash/avie - wpa tkip - I went into network manager and set it all up, It can see the network, but just won't connect..

jay@Ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI4520 PC card Cardbus Controller [104c:ac46] (rev 01)
02:00.2 FireWire (IEEE 1394) [0c00]: Texas Instruments Unknown device [104c:802a] (rev 01)
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
jay@Ubuntu:~$ sudo lshw -C network
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:89:11:02
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:07:eb:31:7b:66
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS
jay@Ubuntu:~$ iwconfig -a
-a        No such device

jay@Ubuntu:~$ iwconfig -a
-a        No such device

jay@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"ash/avie"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:7B:8F:36   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=-55 dBm  Noise level=-95 dBm
          Rx invalid nwid:2858  Rx invalid crypt:127  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7418   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"ash/avie"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:7B:8F:36   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=-55 dBm  Noise level=-95 dBm
          Rx invalid nwid:2858  Rx invalid crypt:127  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7418   Missed beacon:0

---

### Post by nixscripter on 2008-02-22
Please try to connect again, and post the output of ```
ifconfig -a
``` to see if it is getting an IP address from the other end.

And please do it in a [code] block to preserve formatting (those smilies are annoying to decode).

---

