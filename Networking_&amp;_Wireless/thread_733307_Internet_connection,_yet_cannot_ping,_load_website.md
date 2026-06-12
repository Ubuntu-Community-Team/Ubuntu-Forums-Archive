---
title: "Internet connection, yet cannot ping, load websites or download."
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by Desos on 2008-03-23
I am running Gutsy 7.10 on a dell inspiron 6400. Up until yesterday wireless networking worked pretty much flawlessly. Yesterday evening I completely uninstalled firestarter (everything still worked perfectly).

However, after rebooting,  even though everything I know of that shows some property of any network connections (ifconfig, network manager, /etc/network/interfaces) looked exactly the same but firefox will not show any websites and  when I try and ping my router i get this:

peter@dell:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted



--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4009ms

I the same thing when i try and ping a website.

ifconfig produces this:

peter@dell:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:A4:F2:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:C7:A5:A5  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60 errors:0 dropped:43 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8425 (8.2 KB)  TX bytes:377 (377.0 b)
          Interrupt:16 Base address:0x2000 Memory:efdff000-efdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32335 (31.5 KB)  TX bytes:32335 (31.5 KB)

So far i have tried:
disabling ivp6 (by editing /etc/modprobe.d/aliases),
disabling and renabling wireless,
manualy editing /etc/network/interfaces,
searched the forums for similar problems,
double checked wep key.

I have expended my limited repertoire of things to do when ubuntu breaks so I am completely stuck. 

Has anyone had similar problems and resolved them, or have any idea what I can do or do I have to reinstall?

---

