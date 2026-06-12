---
title: "[SOLVED] Continuing wireless problems with D-Link sans operator"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by Bobrm2 on 2007-11-05
I have moved from Xp pro to Linux (Gutsy) and am having spent several days on two problems, that I have been unable to solve. Setting up a wireless network, and getting the HP PSC 2400 to be seen by the Ubuntu 7.10 program.  I am starting to believe that the two problems are connected??

 I bridged the Speed Stream 4200 modem (new a month ago) and have new D-link WBR-1310 router along with, also new, WDA-1320 adapter installed withing the Ubuntu box. This works with the windows operating system.
  In order to connect with the internet, I am using wired connection(s) to the back of the router. Security is set with WPA hex, and password was entered, (now this morning, I am unable to reenter the password.)
   
  Continue to search for information. Any help appreciated. I have additional information, but don´t know what is needed/wanted in order to solve this problem. The following is added at the suggestion from another link. I do not understand it??

Bob

bob@Bob&#347;:~$ sudo lshw -C network
[sudo] password for bob:
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:b7:f9:17
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.0.101 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:19:21:ba:78:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
bob@Bob&#347;:~$ sudo iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"MSHOME00"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:F0:55:54:7F   
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:8704-4847-76   Security mode:restricted
          Power Management:off
          Link Quality=39/70  Signal level=-54 dBm  Noise level=-93 dBm
          Rx invalid nwid:10  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

bob@Bob&#347;:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1C:F0:55:54:7F
                    ESSID:"MSHOME00"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-53 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

eth0      Interface doesn't support scanning.

bob@Bob&#347;:~$ 


	Bob.

---

