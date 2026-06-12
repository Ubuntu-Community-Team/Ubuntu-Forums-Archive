---
title: "Wired network problem in Ubuntu (gusty)"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by Maverick._awp on 2007-11-26
Hello,

I am on a wired network using a PPPoE connection. The problem I have, is that ubuntu (gusty) configures all my LAN applications (Games, Messengers, etc.) to use my ppp0 address, and not my eth0 address. Hence, the other LAN boxes take a lot of time to show up. This is the only problem keeping me from using Ubuntu full-time. If I try doing a ping sweep with nmap, I can see them up. Below is most of the information you will be needing...

Code:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
25.1.1.2        *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 eth0
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0




Code:

eth0      Link encap:Ethernet  HWaddr 00:19:21:24:AE:F5  
          inet addr:10.20.60.91  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7303269 (6.9 MB)  TX bytes:631689 (616.8 KB)
          Interrupt:20 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38924 (38.0 KB)  TX bytes:38924 (38.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:203.115.85.237  P-t-P:25.1.1.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2136895 (2.0 MB)  TX bytes:309114 (301.8 KB)


Code:

 /etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet static
address 10.20.60.91
netmask 255.0.0.0

auto eth0

Code:

Windows IP Configuration



        Host Name . . . . . . . . . . . . : MAV

        Primary Dns Suffix  . . . . . . . :

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . :

        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth

ernet NIC

        Physical Address. . . . . . . . . : 00-19-21-24-AE-F5

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 10.20.60.91

        Subnet Mask . . . . . . . . . . . : 255.0.0.0

        Default Gateway . . . . . . . . . :



PPP adapter Pacenet:



        Connection-specific DNS Suffix  . :

        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface

        Physical Address. . . . . . . . . : 00-53-45-00-00-00

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 203.115.85.237

        Subnet Mask . . . . . . . . . . . : 255.255.255.255

        Default Gateway . . . . . . . . . : 203.115.85.237

        DNS Servers . . . . . . . . . . . : 203.115.71.66

                                            203.115.81.38

        NetBIOS over Tcpip. . . . . . . . : Disabled

Help will be much appreciated....

Thanks in advance...

---

