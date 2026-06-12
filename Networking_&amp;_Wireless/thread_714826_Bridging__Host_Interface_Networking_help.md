---
title: "Bridging / Host Interface Networking help"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by ulver on 2008-03-04
Am running ubuntu desktop and have installed virtualbox and I need that other computers on my private network can conncet to the guest OS so i tried to setup bridgin, this is what I did:

sudo tunctl -t tap1 -u "user"   
sudo brctl addbr br0         	       -> creating br0 virtual bridge

sudo ifconfig eth0 0.0.0.0 promisc     -> making the real network interface promiscous so that it captures all the packets

					
sudo brctl addif br0 eth0              -> linking real interface to the just created bridge

sudo ifconfig br0 10.0.0.33            -> assigning address to the bridge 

sudo brctl addif br0 tap1              -> linking tap1 to the bridge

sudo ifconfig tap1 up                  -> activating tap1

sudo chmod 0666 /dev/net/tun           -> permission change of the tun device
					  configure the virtual client with a address of the same submask.

Promiscous mode has to be set at every startup

Problem 1)
Cant ping (the main) 10.0.0.200 (project) server, no access to network, checked the routing table, no valid default route specified

SOLVED with
sudo route add default gw project

Problem 2)
Have local network connectivity no access to public network. Can ping all host on private network.

this is my ifconfig:
br0       Link encap:Ethernet  HWaddr 00:0B:6A:CF:65:D7  
          inet addr:10.0.0.25  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fecf:65d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3732 (3.6 KB)  TX bytes:4963 (4.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:0B:6A:CF:65:D7  
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fecf:65d7/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:1820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111979 (109.3 KB)  TX bytes:21949 (21.4 KB)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:336 (336.0 b)  TX bytes:336 (336.0 b)

tap1      Link encap:Ethernet  HWaddr 00:FF:52:49:E9:2F  
          inet6 addr: fe80::2ff:52ff:fe49:e92f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:199 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Have removed the bridge now have access to all networks, please help.

---

### Post by ulver on 2008-03-05
bump

---

### Post by SpaceTeddy on 2008-03-05
i have never worked with virtual box - but what does the tap device do in there ? is that used by virtualbox to emulate the network card which is connectied to the vm's subnet ?

acctually, your setup looks rather fine... i just have a few question tiny questions - why do you set the default gateway ? The default GW is used when there is no matching route to anywhere else - i.e. it should always point to the internet (or rather, the device which connects to the internet). 
If the network cards are bridged, then there is not need for a default gw - since the two network cards will be joined as one and anything comming in will be automaticially forwarded between the two regardless of any route.

also, why has eth0 still got an ip ? if it is bridged together with tap1, then it should not have it's own ip - only the bridged device gets one. furthermore, eth0 is in promisc mode, but tap1 is not - i think that one need to me in promisc aswell.

---

### Post by ulver on 2008-03-05
> **SpaceTeddy said:**
> i have never worked with virtual box - but what does the tap device do in there ? is that used by virtualbox to emulate the network card which is connectied to the vm's subnet ?


The TAP device as I figured is a virtual ethernet network device.

> **SpaceTeddy said:**
> 
acctually, your setup looks rather fine... i just have a few question tiny questions - why do you set the default gateway ? The default GW is used when there is no matching route to anywhere else - i.e. it should always point to the internet (or rather, the device which connects to the internet). 
If the network cards are bridged, then there is not need for a default gw - since the two network cards will be joined as one and anything comming in will be automaticially forwarded between the two regardless of any route.


I need the default gw because we are on a private network the has internet access over the 10.0.0.200 (project) server.

> **SpaceTeddy said:**
> 
also, why has eth0 still got an ip ? if it is bridged together with tap1, then it should not have it's own ip - only the bridged device gets one. furthermore, eth0 is in promisc mode, but tap1 is not - i think that one need to me in promisc aswell.

I removed the ip from eth0 and set the tap1 device in promisc mode but still not working, have just access to local network and the server but no internet :(

Here is my new ifconfig:
```

br0       Link encap:Ethernet  HWaddr 00:0B:6A:CF:65:D7  
          inet addr:10.0.0.33  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20b:6aff:fecf:65d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200556 (195.8 KB)  TX bytes:5614 (5.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:0B:6A:CF:65:D7  
          inet6 addr: fe80::20b:6aff:fecf:65d7/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:103872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28412937 (27.0 MB)  TX bytes:2478360 (2.3 MB)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tap1      Link encap:Ethernet  HWaddr 00:FF:11:66:B1:01  
          inet6 addr: fe80::2ff:11ff:fe66:b101/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2208 errors:0 dropped:830 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4060 (3.9 KB)  TX bytes:136334 (133.1 KB)


```

---

### Post by SpaceTeddy on 2008-03-05
i think i missunderstood you... :(

let me straighten out my view of the network before i suggest anything else :)

/-------VM-----\
| VirtualBox | <----> Host Machine <---> project <---> Internet 
\----------------/

IP of virtual Box: 10.0.0.x
ip of Host Machine: 10.0.0.33 (on br0 joined device eth0,tap1)
project: 10.0.0.200

is that your setup ?

---

### Post by ulver on 2008-03-06
Yes, that is what my setup looks like.

---

### Post by SpaceTeddy on 2008-03-06
ok, good :) we are talking about the same thing.

only thing i could possibly think of now is that the vm does not have the correct default gateway set, In this setup, it should be the project server.

otherwise, i am running out of ideas :(

---

### Post by ulver on 2008-03-06
Thank you for your effort, but thats not the main problem, the main problem is that I lose internet connectivity when i setup the bridge.
The project server is running win server 2003 but we will be migrating it soon to a linux server, maybe than the problem will be fixed by itself.

---

