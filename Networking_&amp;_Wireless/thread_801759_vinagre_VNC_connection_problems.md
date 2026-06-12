---
title: "vinagre VNC connection problems"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by shortridge11 on 2008-05-20
I set up a home network and i am using ubuntu desktop to store all my movies, games, etc.  I use Vinagre (the default remote desktop viewer) when my computer is hooked up to a moniter in my room and it works, but when i put it somewhere else it doesn't.  My network topology is:internet connected into a router, router to a switch, computer to switch.  The computer can be seen with Vinagre when it's directly from the router, but only from 1 connection port.  I tried a different cable that went out to a different room and it didn't see it.  It responds to ping, and i can ssh into it, but i can't remote view.  Can someone help?

---

### Post by bluefrog on 2008-05-21
you are talking of one computer. where is the other one?

paste for both

ifconfig
netstat -rn

---

### Post by shortridge11 on 2008-05-21
i've been using my laptop wirelessly connected to the router to access it.

laptop
eth0      Link encap:Ethernet  HWaddr 00:15:c5:1b:3a:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:13:02:99:01:3e  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe99:13e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2613 errors:3 dropped:432 overruns:0 frame:0
          TX packets:2484 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2390236 (2.2 MB)  TX bytes:385209 (376.1 KB)
          Interrupt:16 Memory:dfdff000-dfdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:636400 (621.4 KB)  TX bytes:636400 (621.4 KB)


ian@ian-laptop:~$ netstat -rn 
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1



computer i can't remote control

eth0      Link encap:Ethernet  HWaddr 00:1d:92:28:3f:8d  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fe28:3f8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56922465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29142274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2821590823 (2.6 GB)  TX bytes:1810574365 (1.6 GB)
          Interrupt:20 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

---

### Post by bluefrog on 2008-05-22
sorry, I skipped the fact you could ping and ssh into it.

so
movie server=SRV
your laptop= PC
hub
switch

by cable 
PC-->switch-->server   OK

by wifi
PC-->router-->switch-->server NOT OK

I would say, have a look at why your router is preventing you from accessing your server when connected by wifi (redirect 5900 port eventually)

---

### Post by Peter09 on 2008-05-22
Agree with Bluefrog, some routers have an option to isolate wireless devices from other machines on the network. I should check to see if that on.

PC

---

### Post by shortridge11 on 2008-05-23
actually, here's where it gets weird.  
PC->wireless->router->wired->server = good
PC->wireless->router->wired->switch->wired->server = bad
and then to top things off, i took out the switch and just used a longer cable to connect it so that it was
PC->wireless->router->wired->server, but it was still bad the the only difference is a different physical port and cable.  I haven't switched the physical ports yet because i haven't been home, but that really doesn't make sense to me.  At first i thought maybe a bad cable? but then that doesn't explain my ability to ping and ssh into it...

Also, my PC i'm using to access the server is always wifi, that never changes.

---

