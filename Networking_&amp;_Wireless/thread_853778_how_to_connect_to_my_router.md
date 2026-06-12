---
title: "how to connect to my router?"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by edren on 2008-07-08
testing out a wireless router and hook up my cable modem on it

problem is my desktop ubuntu 8 cannot connect to the net using any of the LAN ports and my laptop which is running WinXP is able to connect thru any of the LAN ports

and once i do a direct connect for my desktop direct connection to the cable modem and restart the modem, my internet connection is back online for my ubuntu

when i right click on my connection icon:
it shows 
"Checked" Wired Network
Connect to 802.1X Protected Wired Network
Manual Configuration

under my network setting:
on the Wired Connection, it is on Roaming Mode

during my desktop connected to the Router lan port, i cant get any connection and i have searched over regarding abt connection issue but couldnt find a exact solution

I have VMware installed in my ubuntu environment

really doesnt want to switch back to windows since i got use to ubuntu, just only wanted to setup a shared internet connection using the wireless router. and im a newbie to linux environment as well

thanks!

---

### Post by edren on 2008-07-08
some info about the direct connection now

> eth0      Link encap:Ethernet  HWaddr 00:19:db:65:6b:d3  
          inet addr:202.156.180.83  Bcast:202.156.183.255  Mask:255.255.248.0
          inet6 addr: fe80::219:dbff:fe65:6bd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2476116 (2.3 MB)  TX bytes:425364 (415.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:852 (852.0 B)  TX bytes:852 (852.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.128.1  Bcast:172.16.128.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.48.1  Bcast:192.168.48.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by edren on 2008-07-08
thanks for those who read and try to help.

i have resolve the connection by flashing my router firmware and reset it to factory default.

all ends well..

:guitar:

---

