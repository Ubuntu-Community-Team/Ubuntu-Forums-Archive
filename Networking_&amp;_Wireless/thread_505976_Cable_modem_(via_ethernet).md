---
title: "Cable modem (via ethernet)"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by ravsas3 on 2007-07-21
I have edubuntu-6.06 installed on my PC (PIII 184MB RAM), because of higher sys requirements with ubuntu or kubuntu.
iam using Sis900 Ethernet card and cable modem (Motorola SB5100) to connect to internet(broadband) in winxp. somehow iam unable to do that same using ubuntu. I had the computer connected to my cable modem during install and I hoped that the networking would be setup automatically, because I'm a complete noob.
I have been booting the computer and logging in while connected to my cable modem but a network monitor applet shows activity and so do the lights on my modem but when I try to access the internet using browser it shows error downloading the page!!.
from the forums i gathered that i have to do these things and so i did:

   1. enable DHCP in the network settings applet(system>administartion>networ)
   2. put the modem in stand by and run dhclient it gave me an ip after that turned the modem on
   3. ran pppoeconf and supplied username and passwd that i use in xp for connection
   4. after that pon dsl-provider

i don't know if i got it wrong, heres how my connection works in xp:
i am giving you a read-out of my 'network connections' in windows
[IMG]http://www.geocities.com/ravsas3/prob.gif[/IMG]
as you can see that the computer says that it is using a pppoe device for connecting to internet and i did run pppoeconfig in Linux but to no avail...i can't even ping any outside servers(tried google 216.239.37.99) of course the i can get to the cable modem's configuration tool (192.168.100.1). i even tried turning off the acpi (as suggested at the boot time, sis900ethernet card)
ipconfig of xp:
Ethernet adapter Local Area Connection:

Connection-specific DNS Suffix . :
IP Address. . . . . . . . . . . . : 192.168.100.22
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . :

PPP adapter YOU TELE:

Connection-specific DNS Suffix . :
IP Address. . . . . . . . . . . . : 123.201.73.88
Subnet Mask . . . . . . . . . . . : 255.255.255.255
Default Gateway . . . . . . . . . : 123.201.73.88

And the connection properties in windows are:

Device name WAN Miniport (PPPOE)
Device Type PPPoE
Server Type PPP
Transports TCP/IP
Authentication PAP
Compression (none)
PPP multilink framing Off
Server IP address 203.109.89.129
Client IP address 123.201.73.88

please help me out!!
thanks in advance

---

### Post by djdicbob on 2007-07-21
In a teminal window/shell on Ubuntu....run these commands and post the output!

```
ifconfig
```
```
route
```


Also, look up the power off reset procedure for the modem.  Many times the client MAC address does not reset until the power is off!

---

### Post by ravsas3 on 2007-07-23
thank you for the reply
here's the output you asked
```
eth0      Link encap:Ethernet  HWaddr 00:D0:09:FE:8B:CA  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69889 (68.2 KiB)  TX bytes:3494 (3.4 KiB)
          Interrupt:11 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2740 (2.6 KiB)  TX bytes:2740 (2.6 KiB)


```
and heres the output for route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```
this output was taken just after booting
no 'pon' or anything
[COLOR="Red"]HURRAY!! PROBLEM SOLVED!![/COLOR]
and after 'pon dsl-provider'
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:D0:09:FE:8B:CA
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9511856 (9.0 MiB)  TX bytes:751958 (734.3 KiB)
          Interrupt:11 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2840 (2.7 KiB)  TX bytes:2840 (2.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:123.201.73.47  P-t-P:203.109.89.129  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:21900 (21.3 KiB)  TX bytes:4090 (3.9 KiB)

ppp1      Link encap:Point-to-Point Protocol
          inet addr:123.201.73.2  P-t-P:203.109.89.129  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:11424 (11.1 KiB)  TX bytes:14951 (14.6 KiB)

ppp2      Link encap:Point-to-Point Protocol
          inet addr:123.201.73.88  P-t-P:203.109.89.129  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:6049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:7226663 (6.8 MiB)  TX bytes:580646 (567.0 KiB)

```

and route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
203.109.89.129  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
203.109.89.129  0.0.0.0         255.255.255.255 UH    0      0        0 ppp1
203.109.89.129  0.0.0.0         255.255.255.255 UH    0      0        0 ppp2
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp2
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```
so thats it, thanks a lot djdicbob!!
if anyone needs any clarification dealing with this problem post in this thread and since i subscribed to this i will try to help you out

---

