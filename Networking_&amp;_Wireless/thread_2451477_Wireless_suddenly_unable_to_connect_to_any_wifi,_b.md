---
title: "Wireless suddenly unable to connect to any wifi, but hotspotting via a tablet is ok"
date: 2020-10-05
forum: Networking &amp; Wireless
---

### Post by Federico_Carta on 2020-10-05
Hello, I would like to ask some help with the following problem.

I have ubuntu 18.04, running on a Lenovo Legion Y520 laptop. My wireless connection has always worked perfectly, until last friday.
Now, it is behaving strangely. I can see the different wi-fi connections (like ex Eduroam, in my university), but I can not connect to any of them. I am afraid the problem is not related to wrong "username password", as I cannot connect even to free connections. Oddly this morning everything was fine and I could connect again, but after few hours it disconnected, and now I cannot connect anymore.
Even more strangely, I can connect to any connection by using a tablet or a mobile phone. Furtheremore, if I connect with the tablet and then I hotspot the laptop, then I can connect through that. But directly with the laptop I can not connect.

I post here the output of some commands.

1) "lshw -c network" gives 

  *-network                 
       description: Wireless interface
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: c8:3d:d4:f1:19:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-118-generic firmware=N/A ip=192.168.43.211 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:131 ioport:4000(size=256) memory:a4100000-a4103fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 10
       serial: 54:e1:ad:2d:00:a4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:3000(size=256) memory:a4004000-a4004fff memory:a4000000-a4003fff

2) "lspci" gives

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 05)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 05)
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
00:14.0 USB controller: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Thermal Subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 (rev 31)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #2 (rev f1)
00:1c.2 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #3 (rev f1)
00:1c.3 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #4 (rev f1)
00:1f.0 ISA bridge: Intel Corporation HM175 Chipset LPC/eSPI Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller (rev 31)
00:1f.3 Audio device: Intel Corporation CM238 HD Audio Controller (rev 31)
00:1f.4 SMBus: Intel Corporation 100 Series/C230 Series Chipset Family SMBus (rev 31)
01:00.0 3D controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] (rev a1)
02:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)


3) "iwconfig" gives

wlp3s0    IEEE 802.11  ESSID:"AndroidAP9412"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 06:B4:29:11:05:C5   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: on
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2666   Missed beacon:0

lo        no wireless extensions.

enp4s0    no wireless extensions.


******************************
Does anyone have any idea about how to possibly solve this? In particular I am very puzzled. I thought maybe a driver issue, but I can't explain why it randomly happened last week. Also another puzzling thing to me is that if I connect with the tablet and then hotspot the laptop everything works, while directly from the laptop it does not.

Thank you very much

---

### Post by TygerTung on 2020-10-06
Does anything improve on a hard restart? My laptop has wifi which randomly stops working and has to be hard restarted. It was OK for years, but maybe with a new kernel update it has gone weird?

---

