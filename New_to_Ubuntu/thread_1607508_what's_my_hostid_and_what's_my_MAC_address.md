---
title: "what's my hostid ??and what's my MAC address??"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by zeuso0 on 2010-10-27
[B]If I type "hostid" in terminal ,it gave me 007f0101
but if I type ifconfig. there is one appeared as HWaddr 00:15:c5:46:57:8a  in eth0; and one HWaddr 00:13:02:ca:f5:5f  in wlan.

which one on earth is my hostid ??/
and what is my flex hostid???[/B]
:(

eth0      Link encap:Ethernet  HWaddr 00:15:c5:46:57:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2540 (2.5 KB)  TX bytes:2540 (2.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:ca:f5:5f  
          inet addr:192.168.18.10  Bcast:192.168.18.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:feca:f55f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6534404 (6.5 MB)  TX bytes:2123008 (2.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-CA-F5-5F-35-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by GabrielYYZ on 2010-10-27
HWaddr = MAC address, so you have eth0, wlan0 and that third one wmaster0, which i don't even recognize (probably some wireles thing i'm oblivious to)

as for the host ID, if i type it in terminal it gives me a sequence similar to the one you posted, but i'm thinking "maybe you're looking for hostname, not hostID?" what do you need hostID for?

---

### Post by Iowan on 2010-10-27
According to the **man** page: > hostid - print the numeric identifier for the current host (My machine also gives 007f0101 as a response to **hostid**.)

---

### Post by zeuso0 on 2010-10-27
> **GabrielYYZ said:**
> HWaddr = MAC address, so you have eth0, wlan0 and that third one wmaster0, which i don't even recognize (probably some wireles thing i'm oblivious to)

as for the host ID, if i type it in terminal it gives me a sequence similar to the one you posted, but i'm thinking "maybe you're looking for hostname, not hostID?" what do you need hostID for?


So i have three MAC address???  but which one am i accually using?? i am using wireless right now. and it appears that wlan has a ip address allocated for me. So does that mean my MAC address to be recognized by the Internet is  the wlan0 's MAC address??

I need to know it to resolve my license issue. :(

Thnks for the help
JOE

---

### Post by sandyd on 2010-10-27
> **zeuso0 said:**
> So i have three MAC address???  but which one am i accually using?? i am using wireless right now. and it appears that wlan has a ip address allocated for me. So does that mean my MAC address to be recognized by the Internet is  the wlan0 's MAC address??

I need to know it to resolve my license issue. :(

Thnks for the help
JOE

yes and no.
the mac address regonized by the internet is your DSL/Cable Modem's

---

### Post by zeuso0 on 2010-10-27
Thanks for the replies/

I found the solution.

the command is "lmutil lmhostid"

---

