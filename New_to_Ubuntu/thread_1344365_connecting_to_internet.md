---
title: "connecting to internet"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by jammic on 2009-12-02
I am new to ubuntu, just installed today. I am connected (wired) to a linksys which is connected to a dsl modem. I can't get on the internet. Can someone help?

---

### Post by Zzl1xndd on 2009-12-02
I assume that you are connecting through a Linksys router, then to a DSL modem? Can any of your Other machines access? If not can you advise if your DSL provider is using PPPoE?

---

### Post by alphacrucis2 on 2009-12-02
> **jammic said:**
> I am new to ubuntu, just installed today. I am connected (wired) to a linksys which is connected to a dsl modem. I can't get on the internet. Can someone help?

Start up the terminal under Accessories and type:


```
ifconfig
```

Post the output here

---

### Post by jammic on 2009-12-03
my windows machine can access the internet fine and yes my linksys runs from the dsl modem. this is the dsl modem config.
 
 
**[SIZE=4]General Status[/SIZE]** 
[FONT=verdana][SIZE=1]Connection:[/SIZE][/FONT] Connected
[FONT=verdana][SIZE=1]Mode: PPPoA[/SIZE][/FONT]
[FONT=verdana][SIZE=1]IP Address: 75.174.92.110[/SIZE][/FONT]
[FONT=verdana][SIZE=1]Subnet Mask:255.255.255.255[/SIZE][/FONT]
[FONT=verdana][SIZE=1]Gateway: 67.41.38.206[/SIZE][/FONT]
[FONT=verdana][SIZE=1]DNS #1: 205.171.3.25[/SIZE][/FONT]
[FONT=verdana][SIZE=1]DNS #2: 205.171.2.25[/SIZE][/FONT]
[FONT=verdana][SIZE=2]**LAN**[/SIZE][/FONT] 
[FONT=verdana][SIZE=1]IP Address:192.168.0.1[/SIZE][/FONT]
[FONT=verdana][SIZE=1]Net Mask:255.255.255.0[/SIZE][/FONT]
[FONT=verdana][SIZE=1]DHCP Server: on[/SIZE][/FONT]

---

### Post by jammic on 2009-12-03
this is what i get when i type ifconfig:
 
[FONT=Calibri][SIZE=3]eth0         Link encap:Ethernet HWaddr 00:0c:76:1b:94:4f[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet addr: 192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet6 addr:fe80::20c:76ff:fe1b:944f/64 Scope:Link[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX packets:1576 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX bytes:433665 (433.6 KB) TX bytes:101696 (101.6 KB)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Interrupt:23 Base address:0x2000[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]lo            Link encap:Local Loopback[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]                inet addr: 127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                RX packets:4 errors:0 dropped:0 overrunns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                Collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]                RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)[/FONT][/SIZE]

---

### Post by jammic on 2009-12-03
**Re: connecting to internet** 
this is what i get when i type ifconfig:

[FONT=Calibri][SIZE=3]eth0 Link encap:Ethernet HWaddr 00:0c:76:1b:94:4f[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet addr: 192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet6 addr:fe80::20c:76ff:fe1b:944f/64 Scope:Link[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX packets:1576 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX bytes:433665 (433.6 KB) TX bytes:101696 (101.6 KB)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Interrupt:23 Base address:0x2000[/SIZE][/FONT]

[FONT=Calibri][SIZE=3]lo Link encap:Local Loopback[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]inet addr: 127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]RX packets:4 errors:0 dropped:0 overrunns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)[/FONT][/SIZE]

---

### Post by alphacrucis2 on 2009-12-03
> **jammic said:**
> **Re: connecting to internet** 
this is what i get when i type ifconfig:

[FONT=Calibri][SIZE=3]eth0 Link encap:Ethernet HWaddr 00:0c:76:1b:94:4f[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet addr: 192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]inet6 addr:fe80::20c:76ff:fe1b:944f/64 Scope:Link[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX packets:1576 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]TX packets:1116 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]RX bytes:433665 (433.6 KB) TX bytes:101696 (101.6 KB)[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Interrupt:23 Base address:0x2000[/SIZE][/FONT]

[FONT=Calibri][SIZE=3]lo Link encap:Local Loopback[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]inet addr: 127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]RX packets:4 errors:0 dropped:0 overrunns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)[/FONT][/SIZE]

Looks ok - even shows data has been sent and received over eth0. 

What does:

```
route -n
```

and 

```
cat /etc/resolv.conf
```

give? Note that one of the lines output by route -n should have 0.0.0.0 listed under the destination heading. On that line, the next field headed Gateway should read 192.168.1.X where X will be some number between 1 & 254 inclusive. That is your default gateway. Try:

```
ping 192.168.1.X
```

Substituting the correct value for X and see if your gateway replies. It is possible that some sort of access control on your router is blocking connections.


EDIT: Very curious. I just noted that the LAN setting on your DSL box you posted above says:

IP Address:192.168.0.1
Net Mask:255.255.255.0

Which is a different subnet to what your linux box has. This might be ok if your linksys is running as a router rather than just a switch. Another check you can do is fire up the command prompt on your windows box and see what addressing the windows box has:

```
ipconfig /all
```

---

### Post by jammic on 2009-12-04
**route -n:**
 
Kernal IP routing table
Destination   Gateway      Genmask      Flags  Metric Ref   Use Iface
192.168.1.0   0.0.0.0      255.255.255.0   U       1       0    0 eth0
169.254.0.0   0.0.0.0     255.255.0.0       U    1000     0    0 eth0
0.0.0.0      192.168.1.1    0.0.0.0          UG       0       0    0 eth0
 
**cat /etc/resolv.conf:**
 
#Generated by NetworkManager
domain domain.atcdsltmp
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.25
nameserver 192.168.1.1
 
**on windows ipconfig /all:**
 
Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.
C:\Users\ Family>ipconfig /all
Windows IP Configuration
   Host Name . . . . . . . . . . . . : Family-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : domain.actdsltmp
Ethernet adapter Local Area Connection:
   Connection-specific DNS Suffix  . : domain.actdsltmp
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 90-E6-BA-65-AD-5A
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::553d:f2d3:2ec3:7282%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.103(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, December 03, 2009 1:48:03 PM
   Lease Expires . . . . . . . . . . : Friday, December 04, 2009 7:57:50 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 244377274
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-12-9C-54-36-90-E6-BA-65-AD-5A
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
Tunnel adapter isatap.domain.actdsltmp:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : domain.actdsltmp
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Teredo Tunneling Pseudo-Interface:
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:30a1:ae2:b451:a391(Prefe
rred)
   Link-local IPv6 Address . . . . . : fe80::30a1:ae2:b451:a391%13(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled
Tunnel adapter 6TO4 Adapter:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

---

