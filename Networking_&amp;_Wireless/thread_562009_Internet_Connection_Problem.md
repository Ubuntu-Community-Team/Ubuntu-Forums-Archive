---
title: "Internet Connection Problem"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by jaywalker13 on 2007-09-28
I have accidentally changed something in my internet connection and now can no longer connect to the internet.

The computer is dual boot with Windows XP which works fine with the wireless access point. I also have an old Mac on the same modem and it works fine with an ethernet connection.

When I first set up my Dell Inspiron 9300 laptop with Ubuntu 7.04, it all came together very easily, so I could not really work out what I had done right to make it work. Yesterday I took my laptop to another site and tried to use it to connect to the internet, thus changing some settings. Now I can't connect to the internet, even though I THINK I have have changed all the settings back to the way they were - as far as I can.

I use a wireless access point connected to an adsl modem. I selected static IP address in the Manual Network Configuration screen.

I set the wireless connection on eth1 as follows:

Address: 192.168.1.11
Subnet was supplied by default: 255.255.255.0
Gateway 192.168.1.11

Security is set to WEP hex.

I had the ethernet connection eth0 disabled as I have found that it sometimes caused problems with the wireless connection. Using manual configuration, I don't know how to disable this. I untick the box that shows it to be enabled in the manual connection screen, but when I reboot the computer, it comes up as being activated.

I tried connecting using ethernet, but that does not work either, even though I used the same IP address as before. (192.168.1.100)

Now I can't even connect to the modem via 127.168.1.1. It won't work whether I use the ethernet or the wireless connection. This works on the Mac (which I am using for this) and on Windows.

Essentially, using the manual configuration does not seem to be doing anything. I don't know how to make any changes to the settings other than via this screen.


The following vast detail is the result of doing:

1. lspci -nn
2. iwconfig
3. iwlist scan
4. ifconfig

Any advice appreciated.

Jay

------------------------------------------------------------------------------------
lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV41.8 [GeForce Go 6800] [10de:00c8] (rev a2)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)

---------------------------------------------------------------
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"walter58"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:3B:A0:86   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-26 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
----------------------------------------------------------------------------
iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:95:3B:A0:86
                    ESSID:"myessid"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-28 dBm  
                    Extra: Last beacon: 3496ms ago
----------------------------------------------------------------------------

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:43:71:12:FA  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:03:D4:37  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe03:d437/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:35755 (34.9 KiB)  TX bytes:5290 (5.1 KiB)
          Interrupt:18 Base address:0x8000 Memory:dcffd000-dcffdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31096 (30.3 KiB)  TX bytes:31096 (30.3 KiB)

---

### Post by jaywalker13 on 2007-09-30
OK, I've finally got it working again.

My setup does not like it when eth0 (wired) and eth1 (wireless) are both enabled. From a textbook, got this:

   sudo ifconfig eth0 down

Also had to untick eth0 in manual configuration

Also used the following to set up eth1:

  sudo ifconfig eth1 192.168.1.11 netmask 255.255.255.0 up

Restarted twice and it still works.

Hope this is useful to someone else.

Jay :lolflag:

---

