---
title: "Dell XPS 8700 could not wire connect to router"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by greenwin2 on 2013-09-10
Hi, I'm new to linux. I have a new Dell XPS 8700 with Ubuntu 12.04 installed on it. My wireless could connect to my router, but wire could not connect to my router. Can  some body help me?

Thank you very much.


 lshw -C network
 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI ExpressGigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 0c
       serial: b8:ca:3a:80:ee:bb
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_listethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fdautonegotiation
       configuration: autonegotiation=onbroadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:d000(size=256)memory:f0204000-f0204fff memory:f0200000-f0203fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: bc:85:56:30:f0:b5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list romethernet physical wireless
       configuration: broadcast=yesdriver=ath9k driverversion=3.5.0-40-generic firmware=N/A ip=192.168.1.108latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19memory:f0100000-f017ffff memory:f0180000-f018ffff
WARNING: output may beincomplete or inaccurate, you should run this program as super-user.
 
$ iwconfig
 
eth0      no wireless extensions.
 
lo        no wireless extensions.
 
wlan0     IEEE 802.11bgn  ESSID:"Easy Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:C4:78:7B   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:89   Missed beacon:0
 
$ sudo lspci -nn
 
00:00.0 Host bridge [0600]:Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
00:01.0 PCI bridge [0604]:Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16Controller [8086:0c01] (rev 06)
00:14.0 USB controller [0c03]:Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev04)
00:16.0 Communicationcontroller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEIController #1 [8086:8c3a] (rev 04)
00:1a.0 USB controller [0c03]:Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d](rev 04)
00:1b.0 Audio device [0403]:Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller[8086:8c20] (rev 04)
00:1c.0 PCI bridge [0604]:Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1[8086:8c10] (rev d4)
00:1c.2 PCI bridge [0604]:Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3[8086:8c14] (rev d4)
00:1c.7 PCI bridge [0604]:Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8[8086:8c1e] (rev d4)
00:1d.0 USB controller [0c03]:Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26](rev 04)
00:1f.0 ISA bridge [0601]:Intel Corporation Z87 Express LPC Controller [8086:8c44] (rev 04)
00:1f.2 SATA controller [0106]:Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1[AHCI mode] [8086:8c02] (rev 04)
00:1f.3 SMBus [0c05]: IntelCorporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22](rev 04)
01:00.0 VGA compatiblecontroller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Turks PRO [Radeon HD7570] [1002:675d]
01:00.1 Audio device [0403]:Advanced Micro Devices, Inc. [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD6000 Series] [1002:aa90]
03:00.0 Ethernet controller[0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express GigabitEthernet Controller [10ec:8168] (rev 0c)
04:00.0 Network controller[0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)

---

### Post by Panderz on 2013-09-10
Have you tried "ip link set wlan0 up"?

---

### Post by greenwin2 on 2013-09-11
Yes, I tried "ip link set wlan0 up". But nothing happen.

---

### Post by greenwin2 on 2013-09-11
Probem solved. After I install new driver [http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/).

---

### Post by Panderz on 2013-09-11
Good to hear. Make sure to mark solved.

---

