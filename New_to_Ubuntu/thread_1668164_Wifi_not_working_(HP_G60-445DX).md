---
title: "Wifi not working (HP G60-445DX)"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by Raiden8816 on 2011-01-15
Hi all,

My friend just gave me his HP to work on, and to my surprise it only has ubuntu.  However I can't for the life of me get the wifi to work.

Any ideas on how to fix this or commands to run in terminal?

Thanks

---

### Post by wep940 on 2011-01-15
Not being familiar with that product, I would need to know more information first:
 
[LIST]
[*]Go to Applications/Accessories/Terminal and click to open a terminal window
[*]type the following and post the outputs back here for us
[/LIST]             lspci <press enter>  Try to copy only those lines that say something like network, ethernet or wireless in them
 
             lsusb <press enter>
 
             lshs -C network
 
             ifconfig
 
             iwconfig

---

### Post by Raiden8816 on 2011-01-16
Lspci


00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)


Lsusb
Bus 

004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


ifconfig


eth2      Link encap:Ethernet  HWaddr 00:1f:16:da:eb:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4368 (4.3 KB)  TX bytes:4368 (4.3 KB)

wlan2     Link encap:Ethernet  HWaddr 00:25:56:1a:46:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig


lo        no wireless extensions.

eth2      no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off

---

### Post by wep940 on 2011-01-16
Hum, I *thought* the ath5k module was supposed to drive your Atheros AR5001 wireless adapter.
 
Could you also post the output of:
 
lsmod | grep ath5k
 
so we can see if that module is loaded or not.

---

### Post by wep940 on 2011-01-17
Ooopppsss - I think that may be ath4k instead (not sure).  At any rate, have you checked the Atheros site for you device to see if there is a Linux driver available?  If none is available, then you will probably need to use ndiswrapper.  That requires Windows XP (only) driver files (.inf and .sys) for your adapter matching the architecture - 32 bit for 32 bit ubuntu (the default) and 64 bit for 64 bit ubuntu. 
 
If you decide to use ndiswrapper, post back for instructions.  Most of the how-to's for ndiswrapper seem to be out of date and make things way too complicated than they need to be.

---

### Post by wep940 on 2011-01-17
Jujst a simple search on the net for linux ar5001 driver turned this up - the link right to atheros for your adapter.  It claims the driver download is also for Linux.
 
[http://www.bioticaindia.com/ar5001.html](http://www.bioticaindia.com/ar5001.html)

---

