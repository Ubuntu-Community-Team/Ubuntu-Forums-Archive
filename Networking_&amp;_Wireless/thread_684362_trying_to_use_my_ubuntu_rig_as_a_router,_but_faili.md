---
title: "trying to use my ubuntu rig as a router, but failing"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by footballstevo75 on 2008-02-01
Hello all, new poster here.
Have been plugging around in ubuntu recently. Have apache set up securely and love it :)
Now I am trying to use that same rig as a router.
I have my onboard ethernet which works fine for receiving the connection. I also have a netgear fa311 which I want to run to a router.
I installed webadminm but am confused on how to use.
Below are the results of ifconfig from the terminal. Eth0 is receiving the connection and that works, but I want to forward that connection to Eth1 and then connect Eth1 to a router. So use ubuntu as a router to a router. 
(IP address removed from Eth0)
Please help, so confused on how to set this up.
" eth0      Link encap:Ethernet  HWaddr 00:13:D4:FF:0C:14  
          inet addr:  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:feff:c14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1298904 (1.2 MB)  TX bytes:138502 (135.2 KB)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:14:6C:75:E9:1E  
          inet6 addr: fe80::214:6cff:fe75:e91e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4140 (4.0 KB)  TX bytes:468 (468.0 b)
          Interrupt:21 Base address:0x4400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:581548 (567.9 KB)  TX bytes:581548 (567.9 KB)
"

---

### Post by ssuehr on 2008-02-01
In general terms, you'd need to set up eth1 with an IP address which is on a different subnet than eth0.  From there, have a look at the iproute package.

Steve

---

### Post by footballstevo75 on 2008-02-01
Thanks, but I got if figured out earlier today.

---

### Post by coastdweller on 2008-02-02
I personally would be interested how you did it?

The thread is useless without the end :(

---

