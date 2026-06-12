---
title: "Wireless D-Link DWL-G630"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by wadhwa on 2008-02-03
I am setting up Wi-Fi between Compaq Pressario V-2000 Laptop that has a PCMCIA D-Link DWL-G630 wireless card and a Windows Mobile (HTC Touch). The network works when I boot up the laptop in Windows Vista (I have a dual boot) but when I reboot in ubuntu 7.10 the network is not getting configured. Here is the output of iwconfig

ath0      IEEE 802.11g  ESSID:"new-sandy"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and here is the output of ifconfig

ath0      Link encap:Ethernet  HWaddr 00:13:46:96:DD:C7  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe96:ddc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:EF:E4:A0  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feef:e4a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2329860 (2.2 MB)  TX bytes:362847 (354.3 KB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35180 (34.3 KB)  TX bytes:35180 (34.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-96-DD-C7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:0 (0.0 b)  TX bytes:32338 (31.5 KB)
          Interrupt:16 

and here is the output of lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
07:00.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)  

What should I do to configure the laptop and the mobile?

---

### Post by Hightide on 2008-02-03
Hi wadhwa

you may be having a driver problem. Are you using madwifi as it is the recommended driver for your device.?  see this [link]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi")

Have you had a look at Kevdogs's wireless [tutorial.]("http://ubuntuforums.org/showthread.php?t=571188") It may help

regards

:)

---

### Post by wadhwa on 2008-02-12
Yes I am using mad wi-fi drivers "ath_pci"  but there seems to be something strange. Why have I got wifi0 showing up as an interface and also ath0. I notice all packets going out to wifi0 interface. If I use ifconfig or iwconfig I can configure ath0 with either static or dyanmic IP.  What is wifi0 inerface? 

This is the output of wifi-radar script....

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/ath0/00:13:46:96:dd:c7
Sending on   LPF/ath0/00:13:46:96:dd:c7
Listening on LPF/eth0/00:c0:9f:ef:e4:a0
Sending on   LPF/eth0/00:c0:9f:ef:e4:a0
Sending on   Socket/fallback
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device ath0 ; Invalid argument.


The SET is failing on ath0. Is this the problem?

---

### Post by Hightide on 2008-02-12
Hi wadhwa

This issue came up in this t[hread]("http://ubuntuforums.org/showthread.php?t=95863") (page 2)


regards

will be back

---

