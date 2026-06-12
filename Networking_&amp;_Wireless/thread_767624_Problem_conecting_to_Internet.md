---
title: "Problem conecting to Internet"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by edward233 on 2008-04-25
Hi,

Trying to setup my DSL connecting using pppoeconf but it returns that "I scanned 2 interfaces, but the Access Concentrator of your provider did not respond".

Im using UBUNTU 8.04 every thing seemed to install alright and is running. 
My modem is a d-link DSL 3001 ADSL ethernet modem
when i checked my windows config this is what I get

Microsoft Windows [Version 6.0.6000]
PPP adapter Broadband Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Broadband Connection
   Physical Address. . . . . . . . . :
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 76.75.125.229(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0
   DNS Servers . . . . . . . . . . . : 216.168.96.10
                                       216.168.96.13
   NetBIOS over Tcpip. . . . . . . . : Disabled

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek RTL8101 Family PCI-E Fast Etherne
t NIC (NDIS 6.0)
   Physical Address. . . . . . . . . : 00-1D-60-9D-15-13
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::d9ef:ca6f:7fec:7b19%8(Preferred)
   Autoconfiguration IPv4 Address. . : 169.254.123.25(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 201334112
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

I know this works I used it for windows and fedora
what am i doing wrong.

Thanks Ed

---

### Post by superprash2003 on 2008-04-25
are you using ipv6 or ipv4?in ubuntu please post results of ifconfig

---

### Post by edward233 on 2008-04-25
Hi my ipconfig is here

eth0      Link encap:Ethernet  HWaddr 00:16:76:0b:56:50  
          inet addr:192.168.2.1  Bcast:255.255.255.255  Mask:0.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1125261 (1.0 MB)  TX bytes:13624 (13.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27736 (27.0 KB)  TX bytes:27736 (27.0 KB)

---

### Post by superprash2003 on 2008-04-26
eth0 = 192.168.2.1 ?? have you manually configured eth0?what is your router's ip address?

---

