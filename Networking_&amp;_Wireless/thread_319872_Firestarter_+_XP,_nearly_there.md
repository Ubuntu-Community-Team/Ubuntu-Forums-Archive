---
title: "Firestarter + XP, nearly there?"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by hereisnowhy on 2006-12-16
Hi, 

I realise there are a lot of questions out there on sharing an internet connection as I have searched the forums and have literally spent all day today trying to find a solution. As I said I have been trying to sort this all day and am really stuck, so would VERY much appreciate some help!!!

I initially started trying to use ICS on XP but have now decided to make my ubuntu box the router, as there seems to be a bit more help available for this setup. I used firestarter to allow internet connection sharing and that seems to be running nicely (after I found you need to link from dhcpd3 to dhcpd)
My setup:

ubuntu box, 2 network cards. One to outside (via cable modem), one via crossover to XP box
XP box, 2 network cards, one disconnected, the other crossover to ubuntu. 

I have a working connection to the outside world, but am having problems with the crossover link. I can see from a tail on /var/log/syslog there is definitely some kind of link between the two machines:

Dec 16 15:12:32 giraffititan dhcpd: DHCPDISCOVER from 00:40:f4:60:a5:1f (marshall) via eth0
Dec 16 15:12:32 giraffititan dhcpd: DHCPOFFER on 192.168.0.254 to 00:40:f4:60:a5:1f (marshall) via eth0
Dec 16 15:12:36 giraffititan dhcpd: DHCPDISCOVER from 00:40:f4:60:a5:1f (marshall) via eth0
Dec 16 15:12:36 giraffititan dhcpd: DHCPOFFER on 192.168.0.254 to 00:40:f4:60:a5:1f (marshall) via eth0
Dec 16 15:12:44 giraffititan dhcpd: DHCPDISCOVER from 00:40:f4:60:a5:1f (marshall) via eth0
Dec 16 15:12:44 giraffititan dhcpd: DHCPOFFER on 192.168.0.254 to 00:40:f4:60:a5:1f (marshall) via eth0
Dec 16 15:13:01 giraffititan dhcpd: DHCPDISCOVER from 00:40:f4:60:a5:1f (marshall) via eth0
Dec 16 15:13:01 giraffititan dhcpd: DHCPOFFER on 192.168.0.254 to 00:40:f4:60:a5:1f (marshall) via eth0

(marshall is the XP machine). This is from before I made the card on the XP machine static, so that it now looks like this (ipconfig)

ip address (i can't cut and past so retyping) : 192.168.0.2
subnet mask : 255.255.255.0
dhcp enabled: no (as i've made it static)
default gateway: 192.168.0.0

My ifconfig is as follows: 

eth0      Link encap:Ethernet  HWaddr 00:D0:70:00:B9:64  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:70ff:fe00:b964/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37138 (36.2 KiB)  TX bytes:29736 (29.0 KiB)
          Interrupt:12 Base address:0xc000 

eth2      Link encap:Ethernet  HWaddr 00:40:F4:60:A2:3C  
          inet addr:81.103.164.167  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::240:f4ff:fe60:a23c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4446294 (4.2 MiB)  TX bytes:541072 (528.3 KiB)
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:737 errors:0 dropped:0 overruns:0 frame:0
          TX packets:737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36936 (36.0 KiB)  TX bytes:36936 (36.0 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

and route gives:

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
81.103.164.0    *               255.255.252.0   U     0      0        0 eth2
default         cpc2-cwma2-0-0- 0.0.0.0         UG    0      0        0 eth2

eth2 is obviously my external link and eth0 the crossover interface.
However I can't ping either machine from the other - the ubuntu box gives me:

PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.1 icmp_seq=2 Destination Host Unreachable
From 192.168.0.1 icmp_seq=3 Destination Host Unreachable
..etc

and similar for the XP box. 
I thought setting the ip addresses myself was a fairly failsafe way of ensuring communication between the two machines - obviously not...

I am at my wits end! Could someone please take the time to help me with this?

---

