---
title: "Howto connect from BSNL's ADSL?"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by balasatya on 2007-10-08
Dear friends,
I can't connect Internet via ADSL From Ubuntu. 

Modem: ** UT-300R2U**

Here is Test Output:
eth0      Link encap:Ethernet  HWaddr 00:16:76:87:3E:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 

eth0:avah Link encap:Ethernet  HWaddr 00:16:76:87:3E:06  
          inet addr:169.254.3.174  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1860 (1.8 KiB)  TX bytes:1860 (1.8 KiB)

sl0       Link encap:Serial Line IP  
          inet addr:192.168.0.1  P-t-P:192.168.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:0 (0.0 b)  TX bytes:1224 (1.1 KiB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.2     0.0.0.0         255.255.255.255 UH    0      0        0 sl0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 sl0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
ok
******************************************************
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

*******************************************
output for tail /var/log/syslog:


Oct  5 18:20:44 ubuntudhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct  5 18:20:54 ubuntudhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Oct  5 18:21:03 ubuntudhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Oct  5 18:21:05 ubuntudhclient: No DHCPOFFERS received.
Oct  5 18:21:05 ubuntudhclient: No working leases in persistent database - sleeping.
Oct  5 18:25:34 ubuntudhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Oct  5 18:25:42 ubuntudhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Oct  5 18:26:02 ubuntudhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct  5 18:26:05 ubuntudhclient: No DHCPOFFERS received.
Oct  5 18:26:05 ubuntudhclient: No working leases in persistent database - sleeping.


Any Help Plz.

---

