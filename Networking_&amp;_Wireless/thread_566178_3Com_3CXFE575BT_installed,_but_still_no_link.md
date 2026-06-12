---
title: "3Com 3CXFE575BT installed, but still no link"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by Zneo on 2007-10-03
The dream: I want to build myself a server, running linux  with 2 NIC's, router/firewall functionality, mythtv, cron jobs and more fun.

The server is a laptop, Compaq Evo N800c, Pentium 4 Mobile, 1,4GHz, 768MB Ram. 

I needed an extra NIC, so I found a 3Com 3CXFE575BT on ebay. I did a couple of google searches and it appears that this card is able to run on linux.

Anyway, the card works fine in the same machine, when it's running Windows, so i figured out I must be able to get it to work.

But I'm a newbie, and it's a though learning curve. 

It appears to work, but there is no link.

The 3c59x module is enabled.

When i run lspci -v, I can see it 
03:00.0 Ethernet controller: 3Com Corporation 3cCFE575BT Megahertz 10/100 LAN CardBus [Cyclone] (rev 01)
        Subsystem: 3Com Corporation 3C575 Megahertz 10/100 LAN Cardbus PC Card
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 2800 [size=128]
        Memory at 54000000 (32-bit, non-prefetchable) [size=128]
        Memory at 54000080 (32-bit, non-prefetchable) [size=128]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 1 

When i run ifconfig, I can see my to NIC's (The card is eth1)
eth0      Link encap:Ethernet  HWaddr 00:08:02:6D:6C:E5  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe6d:6ce5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1993819 (1.9 MiB)  TX bytes:73229 (71.5 KiB)

eth1      Link encap:Ethernet  HWaddr 00:00:86:3B:F7:21  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:90 (90.0 b)
          Interrupt:11  

I notice it doesn't say “RUNNING” at eth1.

If i do a manual configuration, I'm able to ping the local ip, but it's still not running.

root@uevo:~# ifconfig eth1 down
root@uevo:~# ifconfig eth1 192.168.1.4 netmask 255.255.255.0 broadcast 192.168.1.255 up
root@uevo:~# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:00:86:3B:F7:21  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:90 (90.0 b)
          Interrupt:11 

root@uevo:~# ping 192.168.1.4
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
64 bytes from 192.168.1.4: icmp_seq=1 ttl=64 time=0.054 ms

I have tried on Ubuntu 7.04 or Ubuntu Server 6.06 LTS.

What can i do?

Please help!
Zneo

---

### Post by Lambert on 2007-10-03
Explain the desire for two nics and what you want to do? split the traffic amongest the two or have each nic go to different locations (one to the internet and the other to a lan)

also run the terminal command [COLOR="Red"]route[/COLOR] and post output here.

---

### Post by Zneo on 2007-10-04
Hi again, thank you for your time.

The idea is to have one NIC for the internet and another for the internal network. Later on when the NIC is up, I would also like NAT and easy to use firewall interface (i found firestarter, which i will try). 

Right now I connect both NIC to the same internal network. Both are configured as dhcp clients. 

When i look at my netgear router, there is no link to the 3Com NIC. When I look at the 3Com NIC there is no light (it will light up when i booted in windows). I have tried to change the cables, to see if that's the problem, but it's not.

The route table:
[FONT="Courier New"]root@uevo:/home/cvr# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.97.0     *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
172.16.203.0    *               255.255.255.0   U     0      0        0 vmnet1
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth10	eth1[/FONT]

I'm sorry for the confusing vmware server, which is also installed. This is from my ubuntu 7.04. On my ubuntu server 6.06 the problem is the same, without vmware, but to avoid confusing I only post output from the 7.04.

Looking forward for any ideas. Thanks.

---

### Post by Zneo on 2007-10-07
Hi there, still looking for help. Please, I will appreciate any help. Thanks!

:)

---

### Post by Lambert on 2007-10-07
Ok, need to get this straight.

You have two nics in your pc and they both connect to the same router correct?

If you want to use two nics going to two different networks, you have to have them connected to different devices. For example your internet nic connected direct to a modem and the other nic connected to a router setup to your local subnet. Then you set up routes so all internet trafic goes through nic connected to modem and all other traffic to the lan. 

If both are connected to the same router, it all has to go to the subnet of that router and then the router handles traffic from there. In this case you use nic binding where they share the traffic but you can't divide what traffic goes where, that's the routers job.

---

### Post by Zneo on 2007-10-10
Hi again,

thanks for your time.

I'm perfectly aware of that, but right know I just want them to up running, then I can reconnect and reconfigure ip addresses after. But right now there is no physical link on the one. The module seems like it's doing it's job. I can run ifconfig, I can ping the local address, but there is no physical link. The little LED diode in the router and the 3Com card does not light up. 


If i compare one of the lines in from th ifconfig, I can see that another working NIC is saying:
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

while my non working 3Com NIC is:
UP BROADCAST MULTICAST MTU:1500 Metric:1

It's not the cable. It works out of the box when I boot up in windows.

Am I using the right module (3c59x)?

Remember I am a newbie with linux (but not with networks). Hope to get help.

Thank you all!

---

### Post by kevdog on 2007-10-10
Do you want to internet connection share through the second card (ie a bridge setup), or do you want to use it to simply contact other computers on the LAN -- in this case wouldnt you want the two cards on different subnets??

What are the two IP addresses of the two network cards you are trying to use??  Are you assigning static IP addresses to the cards??

---

### Post by Lambert on 2007-10-10
Ok, so let's go back to your route command

> 
default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
default * 0.0.0.0 U 1000 0 0 eth10 eth1


This says that eth0 has a route to your gateway and all traffic will go here. Your eth1 has no gateway (the *) so the kernel doesn't send any traffic over this interface.

If you have two nics that you want to link and connect to the same gatway, you need to bind these, correct? Other wise the routing table says all traffic travels along eth0 as there is no gateway for eth1.

Have you tried to take down eth0 and just run all traffic over eth1? This will prove or disprove that you have a working nic.

```

sudo ifdown eth0
sudo ifdown eth1
sudo ifup eth1

```

Run the previous commands (ifconfig; route) again and see if eth1 is running and you have traffic to the router.

---

