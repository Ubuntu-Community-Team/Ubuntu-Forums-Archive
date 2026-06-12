---
title: "Internet connection sharing"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Kohr-Ah on 2010-03-01
Hi all

I'm trying to share an iBurst internet connection. My setup is as follows:

[XP box]-->eth1[My Ubuntu box]eth0-->[iBurst modem]

So far I've tried Firestarter and Arno's iptables script. I've also attempted to follow the numerous pages of instructions on the web, concerning iptables, but I haven't had any success. The instructions I've tried include having set up ip forwarding and masquerading, but like I said, I've had no success. My Ubuntu box has no problem accessing the web at all. My ifconfig output looks like this:

eth0      Link encap:Ethernet  HWaddr 00:50:fc:fe:90:b0  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fefe:90b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1460147 (1.4 MB)  TX bytes:12411 (12.4 KB)
          Interrupt:16 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 00:11:d8:8a:39:56  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe8a:3956/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3543355 (3.5 MB)  TX bytes:1046531 (1.0 MB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30584 (30.5 KB)  TX bytes:30584 (30.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.208.196.200  P-t-P:41.208.192.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1392  Metric:1
          RX packets:3652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2760617 (2.7 MB)  TX bytes:618094 (618.0 KB)

I'd appreciate any help...

Thanks

---

### Post by 3rdalbum on 2010-03-01
Assuming you're using Ubuntu 8.10 or better, you really don't need to touch IPtables at all. Network Manager can do internet connection sharing.

In Network Manager's "Edit Connection" window, you will see Auto eth0 which is your iBurst, and Auto eth1 which is your other computer. Select Auto eth1 and click Edit. Go to IPv4 Settings and under the Method popup menu, choose "Shared to other computers".

That should be all there is to it. I've noticed on my machine that I have an addition connection that I added (i.e. not an "Auto eth0/1") that seems to be the shared one, so you might possibly need to add an additional one to be the "shared to other computers".

---

