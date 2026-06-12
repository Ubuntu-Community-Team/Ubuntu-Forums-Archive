---
title: "Can't Get wireless connection"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Rybandt on 2010-07-01
Okay, thanks to Realzippy for finding a guide that helped me finally get Ubuntu 10.04 installed perfectly, kudos to you my man:KS. Only one problem left. I don't know if my wireless card works. I don't know how to "scan" for a network. And I have nothing in the top right panel like I use to. I have a Toshiba A505-s6033, and no idea what type of network card is in it.. Anyone know of a fix?

---

### Post by d3ngar on 2010-07-01
Hi,

Even if the wireless card isn't working, you should have a connection icon in the top right. Right click on that and you should be able to 'enable wireless'.

What about the wireless indicator light? Is it on? 

Can you post the output of 'lspci' and also 'ifconfig', please?

Thanks!

---

### Post by Rybandt on 2010-07-01
> **d3ngar said:**
> Hi,

Even if the wireless card isn't working, you should have a connection icon in the top right. Right click on that and you should be able to 'enable wireless'.

What about the wireless indicator light? Is it on? 

Can you post the output of 'lspci' and also 'ifconfig', please?

Thanks!


I know I should have a connection icon in the top right, but I don't :confused:


ryan@ryan:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
04:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
04:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
04:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
04:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
ryan@ryan:~$ 



IFCONFIG

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:6c:3b:bc:1f  
          inet addr:192.168.15.4  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe3b:bc1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:21495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23196154 (23.1 MB)  TX bytes:2789912 (2.7 MB)
          Interrupt:50 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1320 (1.3 KB)  TX bytes:1320 (1.3 KB)

ryan@ryan:~$

---

### Post by bkratz on 2010-07-01
Might be at least worth looking at

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

---

### Post by Rybandt on 2010-07-01
> **bkratz said:**
> Might be at least worth looking at

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

Thank you for that, but I have done updates, so I don't know why its not working :\

---

### Post by bkratz on 2010-07-01
Here is a pretty good thread--especially page 2.

[http://ohioloco.ubuntuforums.org/showthread.php?t=1353049](http://ohioloco.ubuntuforums.org/showthread.php?t=1353049)

---

