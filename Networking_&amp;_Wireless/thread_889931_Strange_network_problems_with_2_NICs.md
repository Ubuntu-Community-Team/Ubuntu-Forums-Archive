---
title: "Strange network problems with 2 NICs"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by ztripez on 2008-08-14
On the attached file is my current network setup at home.

I have 2 separate 100Mbit fiber incomming;
1 goes to my router (a D-Link DI-524UP) and 1 goes directly to my file/web/ftp-server (on eth0).
As you can se the server also connected to the router (on eth1) so the router-clients have access to the files on the server (via SMB),
I have no problems on outgoing trafic on the server or the routed-lan.

Here to my problem;
As soon as i get traffic on the lan (lan <=> eth1) all the incomming traffic (internet => eth0) (such a webserver-visits or ftp-request) the eth0 halts. You can't even ping it, but as soon as the (lan <=> eth1) traffic ends (or if turn of the router or disable the eth1 interface) the eth0 interface start to work again.

Does anyone have any clue what the problem might be, i realy don't have idea.

Help me Obi-wan Kenobi, your my only hope.

---

### Post by wirelessmonkey on 2008-08-14
This will happen if eth1 and eth0 are on the same subnet.

---

### Post by ztripez on 2008-08-14
Hum, ok but how do i sort that? Not that good on networking honestly,



EDIT:
ah nevermind i thought you say that they had to been on the same subnet., got abit confused there.

I've change the subnet on my lan now.. hope it will make things better.

Thanks

---

### Post by ztripez on 2008-08-14
Nope, didn't work. I'd change the subnet from 255.255.255.0 to 255.255.255.128 on the router and i got the same result;
As soon as i enable the eth1, the incoming traffic to eth0 goes down.

:(

---

### Post by bab1 on 2008-08-14
I believe you have a routing loop.  Spanning tree protocol stops the looping.  Spanning tree should NOT be disabled.  Reconfig your wiring (design).  Can you see the loop?

---

### Post by wirelessmonkey on 2008-08-15
> **ztripez said:**
> Nope, didn't work. I'd change the subnet from 255.255.255.0 to 255.255.255.128 on the router and i got the same result;
As soon as i enable the eth1, the incoming traffic to eth0 goes down.

:(

That is your subnet **mask**.
This problem occurs if both interfaces are on the **same** subnet.

If you disregard the mask, and example of 2 interfaces on the same subnet would be:
eth0: 192.168.0.1 subnet 255.255.255.0
eth1: 192.168.0.200 subnet 255.255.255.0

Devices on different subnets:
eth0: 192.168.0.1 subnet 255.255.255.0
eth1: 192.168.5.1 subnet 255.255.255.0


----

If 2 interfaces are on the same subnet, one will probably be filtered unless the interfaces are bridged.

---

### Post by ztripez on 2008-08-15
> **bab1 said:**
> I believe you have a routing loop.  Spanning tree protocol stops the looping.  Spanning tree should NOT be disabled.  Reconfig your wiring (design).  Can you see the loop?

Hum, is it the internet->eth0->eth1->dlink>internet you refer to?
How would i do it otherwise?

Also did some googling on spanning tree protocol and got a very basic understanding on it.

How do i enable spanning tree in ubuntu? how do i configure it?

---

### Post by ztripez on 2008-08-15
> **wirelessmonkey said:**
> That is your subnet **mask**.
This problem occurs if both interfaces are on the **same** subnet.

If you disregard the mask, and example of 2 interfaces on the same subnet would be:
eth0: 192.168.0.1 subnet 255.255.255.0
eth1: 192.168.0.200 subnet 255.255.255.0

Devices on different subnets:
eth0: 192.168.0.1 subnet 255.255.255.0
eth1: 192.168.5.1 subnet 255.255.255.0


----

If 2 interfaces are on the same subnet, one will probably be filtered unless the interfaces are bridged.

Ah everyday you learn something new ;)
Well then thats not the problem since the Lan has a 192.168.0.x series and the eth0 have a public ip (87.96.173.x something) well the router also gets a public ip (87.96.173.x). I also tried to change the ip serie to 192.168.1.x just to try but with the same result.

---

### Post by bab1 on 2008-08-15
> Hum, is it the internet->eth0->eth1->dlink>internet you refer to?

Yes.

> How would i do it otherwise

You don't.  For small networks you should only have one route to the network.

> How do i enable spanning tree in ubuntu? how do i configure it?

It is enabled.  That's why one interface is dropped.  Spanning tree just blocks one of the interfaces to STOP looping.

So, the answer is for you to redesign the network to have only 1 gateway (GW) to the internet.

---

### Post by ztripez on 2008-08-15
Well I see that as a last resort since that would mean i throw 1 of my 100 mbits connection away. 

The whole point with the current setup is not to stress the servers incomming connections with traffic from my LAN, iow bandwith-loss, but still have the server connected to the LAN.

Can't i somehow filter my data so the server dosn't use the eth1 at all on "talking to the internet" and use it only on let's say for an ip-serie (in this case 192.168.0.x). My guts tells me that must go with some iptables-hacking (never done it but it seams fairly simple). Will the spanning tree-thingee bee satifyed with that?

---

### Post by bab1 on 2008-08-15
> The whole point with the current setup is not to stress the servers incomming connections with traffic from my LAN, iow bandwith-loss, but still have the server connected to the LAN.

But it does load the server.  ALL traffic is seen by the servers on both interfaces is inspected.

> Can't i somehow filter my data so the server dosn't use the eth1 at all on "talking to the internet" and use it only on let's say for an ip-serie (in this case 192.168.0.x)

So you are saying everything goes through this filter?  If so does this not meet the criteria of one GW?  It sounds like you want to create a backbone for your LAN.

Edit:  I do see a way to use the 2'nd 100Mbs line.  It involves another router and a separate network that forces the internet traffic to exit the LAN via its own connection.  NO LOOPING.

---

### Post by ilrudie on 2008-08-15
> **bab1 said:**
> But it does load the server.  ALL traffic is seen by the servers on both interfaces is inspected.



So you are saying everything goes through this filter?  If so does this not meet the criteria of one GW?  It sounds like you want to create a backbone for your LAN.

Edit:  I do see a way to use the 2'nd 100Mbs line.  It involves another router and a separate network that forces the internet traffic to exit the LAN via its own connection.  NO LOOPING.

Just change the defualt route on the server so it uses the correct device.
Any thing that is not locally connected to an interface (a.k.a internet bound packets) will go out the default route.
This works because on a small LAN with only 1 subnet a multi-homed server (like yours) should use arp to resolve ips on the lan before it looks at the routing tables.  You can also add a net route for your lan but it shouldn't be necissary.

Also if arp spoofing is enabled eth1 may answer for packets bound for eth0 so you may not actually be able to ping eth0 from your lan (eth1 will respond to your pings instead).  This should not happen with arp spoofing disabled.  I do not know which is the default behavior in Ubuntu.

Post a netstat -rn if you are uncomfortable with this and I can verify that the routing looks correct.

---

### Post by ztripez on 2008-08-15
Todays setup:

100Mbit -> 4 (sometimes more) computer shares this one, uses like IM, torrents, web email etc etc, heavy traffic.

100Mbit -> 1 Server with Ftp- Web-server. It also act like fileserver for the Lan. Heavy-load from outside sources.

The ideal would be to unplug the server from the LAN and just let it act like a stand-alone server. But since my LAN clients need access to the filesystem on the server i can not do that.
A workaround would be a tunnel that goes between the server and the lan through internet (now that's a workaround :P)

An other solution would be to unplugg the D-link and use the Server as gateway instead. I do not whant to do that since that would mean I have to unplug one of my fibers, and that would slow the traffic down severly both for the server and the LAN.
It would also mean i have to buy alot of new hardware (new motherboard to the server since all my PCI/PCIe solts are full (for a third NIC if i want to merge the 2 fibers together somhow), a new router and a wirless-extender), this is not an option.

I can't believe I'm the only one whant/needs to have this kind of setup (or something with similar result).

---

### Post by ztripez on 2008-08-15
> **ilrudie said:**
> Just change the defualt route on the server so it uses the correct device.
Any thing that is not locally connected to an interface (a.k.a internet bound packets) will go out the default route.
This works because on a small LAN with only 1 subnet a multi-homed server (like yours) should use arp to resolve ips on the lan before it looks at the routing tables.  You can also add a net route for your lan but it shouldn't be necissary.

Also if arp spoofing is enabled eth1 may answer for packets bound for eth0 so you may not actually be able to ping eth0 from your lan (eth1 will respond to your pings instead).  This should not happen with arp spoofing disabled.  I do not know which is the default behavior in Ubuntu.

Post a netstat -rn if you are uncomfortable with this and I can verify that the routing looks correct.

Ah, that sound like something I'll need ;)
I have no clue at all where to start to change the default route or how to use arp. My former network-knowleage spans to setup simple lans and wlans (or sometimes if I want to go crasy: do a bridge ;D).

I will do a netstat -rn as soon as i get home from work (or from the afterwork-party I'm attending to ;D) and do some reading on default routing.

Cheers

---

### Post by ilrudie on 2008-08-15
> **ztripez said:**
> Ah, that sound like something I'll need ;)
I have no clue at all where to start to change the default route or how to use arp. My former network-knowleage spans to setup simple lans and wlans (or sometimes if I want to go crasy: do a bridge ;D).

I will do a netstat -rn as soon as i get home from work (or from the afterwork-party I'm attending to ;D) and do some reading on default routing.

Cheers

ARP is already being used.  The server says "what physical address responds to this ip address?" if the ip is on the same network as one of the server's interfaces.  Routing only needs to occur if the destination is on a different network.  

use route del default to delete the current defualt route.
use route add defualt dev eth0

You will need to do this as root (eg use sudo).
Also routing information is temporary in Linux.  If you want to make these static routes permanent you must add them to /etc/networks/interfaces
This generally will go into the same stanza as the interface and be of the form
[INDENT]up <route command>
[/INDENT]
use down <route command> in the same stanza to remove the default route if you take the interface down.

---

### Post by ztripez on 2008-08-16
Omg what a hangover.. brrr

Here is a output from netstat:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
87.96.173.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth1
0.0.0.0         87.96.173.1     0.0.0.0         UG        0 0          0 eth0
```

---

### Post by ztripez on 2008-08-16
Hum, my route outputs:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
87.96.173.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth1
default         1-173-96-87-gw. 0.0.0.0         UG    100    0        0 eth0

```

isn't it abit weird with 2 "default"?

I did as you said with "sudo route del default" but i had to do it twice to remove both default and entered "sudo route add default dev eth0"
and now my 

netstat -rn looks like:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
87.96.173.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0

```

and route:
```
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
87.96.173.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     0      0        0 eth0
```

looks abit cleaner.. now I just need to figure it out what it means ;D.

---

### Post by ztripez on 2008-08-16
It works! both my interfaces are upp and running.. i have traffic on both and **_IT WORKS!_**.
I realy can't belive it.. i'm doing ifconfig over and over just to check again ;D

Man... thanks alot! if you ever come to Gothenburg, Sweden I owe you a beer.

Cheers!

---

### Post by ztripez on 2008-08-16
Err... is it the /etc/networks or the /etc/network/interfaces?

I assume that you ment /etc/network/interfaces..

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0


iface eth1 inet dhcp

auto eth1

```

so my new one would look like this?
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp

auto eth1

up route add add default dev eth0              
down route remove default dev eth0 
```

correct?

---

### Post by ilrudie on 2008-08-16
It should be:

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
[INDENT]up route add add default dev eth0              
down route remove default dev eth0
[/INDENT]auto eth0

iface eth1 inet dhcp
auto eth1


```

---

### Post by ztripez on 2008-08-17
Hum.. i copy/pasted and it didn't work. I still have to set the routing manualy

---

### Post by ilrudie on 2008-08-17
> **ilrudie said:**
> It should be:

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp[INDENT]up route add [COLOR=Red]add[/COLOR] default dev eth0              
down route remove default dev eth0
[/INDENT]auto eth0

iface eth1 inet dhcp
auto eth1


```

Remove the second add.  Sorry about that.  I missed that when I copied your other code over and moved the up/down into the eth0 stanza.

---

### Post by ztripez on 2008-08-30
I forgot to say thank you for the last thing.. :)

Thanks! I't works like a charm

---

