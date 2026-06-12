---
title: "Virtualbox 'host networking' and firestarter problem"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by alkatron on 2008-11-06
Ciao a tutti

I have ubuntu hardy:
Linux alkhm-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

with 2 netcard

eth0      Link encap:Ethernet  HWaddr 00:19:66:02:21:8c  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe02:218c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3036 (2.9 KB)  TX bytes:8336 (8.1 KB)
          Interrupt:219 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:04:76:27:a3:b0  
          inet addr:23.248.51.187  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::204:76ff:fe27:a3b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:440 txqueuelen:1000 
          RX bytes:5078529 (4.8 MB)  TX bytes:761775 (743.9 KB)
          Interrupt:21 Base address:0xc00 

eth1 is connected to internet shared (by firestarter)
eth0 is connected to my lan so that other computer can access internet

Now I installed Sun virtualbox 2.0.4 and have no problem with 1 vbox adapter (eth0 NAT) by wich I can connect to the web.
The problem is the 2 adapter (eth1 host interface) by wich i would like to mount in vbox my ubuntu shares.

I create virtual interface
	VBoxAddIF vbox0 <myname>

I gave it an IP
	ifconfig vbox0 192.168.1.2 netmask 255.255.255.0

inside virtualbox i have 2 card
	eth0 NAT
	eth1 host interface 192.168.1.3

and now the problemi arise:
If I stop firestarter i can ping and see & mount the ubuntu shares from virtualbox but i can't access internet from the lan because it is manage by firestarter..... i think.
With firestarter on, i can access internet from lan and virtualbox but i can't ping and mount the ubuntu shares from virtualbox.

I tried to add policy to firestarter
	allow connection from host 192.168.1.3
	allow service lpp and samba 192.168.1.3
but nothing change

I tried to make the bridge between vbox0 and eth0 on br0 as told in many guides and howtos but as I add eth0 to the br0 the lan is disconnected.

Any ideas?

Thanks to all....and sorry for my english



Alkatron

---

