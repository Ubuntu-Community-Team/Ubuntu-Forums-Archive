---
title: "Wifi nic chooses HOW many IPs ?"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by nicholaspaul on 2007-07-23
I'm setting up yet another machine with Ubuntustudio and a D-Link (forget the model number...) card. 
Most of the computers on the network use a static IP determined by the MAC address of each machine. To set this new thing up, I made DHCP available with a couple of IP addresses free, and let the new machine show up in the router list. 

So far so good, DHCP on ubuntustudio shows up as 192.168.0.120 in the router setup. In previous attempts I got the router to give it 192.168.0.111. Now I'm trying to get it working under DHCP, no statics. 

Clear as mud? 

ifconfig looks like this:

[COLOR="YellowGreen"]
ath0      Link encap:Ethernet  HWaddr 00:0F:3D:A8:C2:69  
          inet addr:192.168.0.120  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:fea8:c269/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3010996 (2.8 MiB)  TX bytes:15969 (15.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79385 (77.5 KiB)  TX bytes:79385 (77.5 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-3D-A8-C2-69-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1735673 errors:0 dropped:0 overruns:0 frame:25729
          TX packets:1604 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:151650418 (144.6 MiB)  TX bytes:91442 (89.2 KiB)
          Interrupt:3 
[/COLOR]

Why are there two IPs, one for ath0 and one for wifi0? Is 192.168.0.111 somehow recorded somewhere and it thinks thats what it should be? 
The other issue is ping 192.168.0.1 (router) returns the result:

192.168.0.111 icmp_seq=3 Destination Host Unreachable
192.168.0.111 icmp_seg=5 Destination Host Unreachable ...etc.

Why, if the router thinks its IP is 192.168.0.120, does ping think it ends in 111? Oh, and I can't connect to ping anything. 

Any questions or pointers would be great! Thanks!

PS I have another machine with the same NIC card in it, it's ifconfig is this:
[COLOR="SlateGray"]ath0      Link encap:Ethernet  HWaddr 00:0F:3D:AB:FE:50  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:feab:fe50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2195192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:663092738 (632.3 MiB)  TX bytes:20986241 (20.0 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11110 (10.8 KiB)  TX bytes:11110 (10.8 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-3D-AB-FE-50-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:471258226 errors:0 dropped:0 overruns:0 frame:32016556
          TX packets:429632 errors:816 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2536160588 (2.3 GiB)  TX bytes:39521225 (37.6 MiB)
          Interrupt:5 Memory:c89e0000-c89f0000 [/COLOR]

---

### Post by nicholaspaul on 2007-07-26
was there something I was missing? I'm just really confused!

---

### Post by nicholaspaul on 2007-07-28
BY the way, I even tried uninstalling/installing (physically) the nic. Nothing happening...

---

