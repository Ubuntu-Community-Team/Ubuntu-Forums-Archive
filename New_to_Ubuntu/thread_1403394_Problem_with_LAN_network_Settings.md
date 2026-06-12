---
title: "Problem with LAN network Settings"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by firoz3321 on 2010-02-10
Finally I installed UBUNTU on my system, thanks to useful guidance.

I cannot connect to internet from UBUNTU. 
I use direct LAN connection without any ROUTER or MODEM.
I set WIRED connection but i can't connect.

I attached the Screenshots and also posted the IP info,

VISTA SETTINGS:
```

Microsoft Windows [Version 6.0.6002]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\Feroze>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::f164:774e:7669:8889%12
   IPv4 Address. . . . . . . . . . . : 172.16.11.97
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 172.16.11.1

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:cf2e:3096:88b:3b28:357a:c70c
   Link-local IPv6 Address . . . . . : fe80::88b:3b28:357a:c70c%10
   Default Gateway . . . . . . . . . : ::

```

UBUNTU Settings:

```
feroze@Home-Pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:c9:1f:39  
          inet addr:172.16.11.97  Bcast:172.16.11.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fec9:1f39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:4009 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4792 (4.7 KB)
          Interrupt:21 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:510 (510.0 B)  TX bytes:510 (510.0 B)

```

Thank You in advance.

---

### Post by Grenage on 2010-02-10
```
Autoconfiguration IPv4 Address. . : 169.254.181.14
```

That's a *"crap, I haven't been given an IP address"* address.  Are you saying it worked on this install?

---

### Post by firoz3321 on 2010-02-10
Sorry Corrected it.

EDIT:
I just now collected info again, while its working.
Is it possible that changing settings in UBUNTU can change the Working in VISTA ?

---

### Post by Grenage on 2010-02-10
No, they are independent.  Is the gateway set on Linux, and the DNS servers specified?

---

### Post by firoz3321 on 2010-02-10
I added the Screen Shots. 
I dont know where to add the Gateways and no idea about the DNS servers.
I'm a newbie to both LINUX and NETWORKING.

---

### Post by Grenage on 2010-02-10
That 'should' work.  Try adding another network and inputting the settings again there, then left-click on the network applet and activate your new connection.  Sometimes the network manager has a flid, see if that does it.

---

### Post by firoz3321 on 2010-02-10
Does this have anything with MY service Provider to do ?

---

### Post by Grenage on 2010-02-10
I can't see why it should, your MAC address will be the same (same hardware) - so there is no reason for your ISP to regard the computer any differently.

---

