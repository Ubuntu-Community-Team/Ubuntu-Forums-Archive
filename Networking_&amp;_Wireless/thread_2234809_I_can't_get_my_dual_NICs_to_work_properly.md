---
title: "I can't get my dual NICs to work properly"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by stevecarter26 on 2014-07-17
Hello,
Really hoping someone can help me out with this. I have a home server that I use for file shares and then secondarily as a plex server, torrent box, mumble server and access to webmin. I have bought an additional Intel NIC as they are supposed to outperform the onboard one.
Onboard ubuntu calls em1
Intel NIC 1 is p1p1

I want to channel all of my internal file sharing over p1p1 so I get the best possible transfer speeds and then I want to channel all the external bound things over em1 so I have separation. To my knowledge it was working fine but then after a recent update it appears to have stopped working!

IFconfig looks like:
```
em1       Link encap:Ethernet  HWaddr 9c:b6:54:04:5b:62  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9eb6:54ff:fe04:5b62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:822433 errors:0 dropped:131303 overruns:0 frame:0
          TX packets:664414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205733028 (205.7 MB)  TX bytes:174352283 (174.3 MB)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:114022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33296955 (33.2 MB)  TX bytes:33296955 (33.2 MB)


p1p1      Link encap:Ethernet  HWaddr 00:1f:29:54:30:84  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:29ff:fe54:3084/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216819 errors:0 dropped:131303 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15410506 (15.4 MB)  TX bytes:9269 (9.2 KB)
          Interrupt:18 Memory:fe8e0000-fe900000
``` 


Network interface file;
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information see interface(s)


# The loopback network interface
auto lo em1 p1p1
iface lo inet loopback


#The primary network interface
# DHCP not needed
# iface em1 inet dhcp
iface em1 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1


#The secondary network interface
#DHCP not needed
#iface p1p1 inet dhcp
iface p1p1 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        gateway 192.168.1.1


#The gimped interface
#DHCP not needed
#iface p1p2 inet dhcp
iface p1p2 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        gateway 192.168.1.1

```

Route command;
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router.asus.com 0.0.0.0         UG    0      0        0 em1
192.168.1.0     *               255.255.255.0   U     0      0        0 em1
192.168.1.0     *               255.255.255.0   U     0      0        0 p1p1

```
I have loosely tried adding a metric to both p1p1 of 10 and em1 of 20 but this seems to stop everything from working, I was thinking that it would work in respect of making p1p1 the "master" and then only traffic directed at em1 would work but it appears not to work like that.

**The eagle eyed will notice there is also p1p2 which as per code seems gimped, it never works and I have deactivated it because it is causing so much trouble.


Any help would be massively appreciated :-)

---

### Post by h.hittini on 2014-07-17
Why don't you create two networks
For example 192.168.1.0/24 for the internal activity and 192.168.2.0/24 for the external one

---

### Post by stevecarter26 on 2014-07-17
> **h.hittini said:**
> Why don't you create two networks
For example 192.168.1.0/24 for the internal activity and 192.168.2.0/24 for the external one

My router is probably going to stop me from doing that as it only supports a single subnet. I understand what you mean but don't know how well that would work for me.


What about? Setting metric 10 on p1p1 and metric 20 on em1 then removing the gateway IP from p1p1.
Would that only give p1p1 LAN access as no external gateway and em1 would retain it's gateway giving it external access?

---

### Post by h.hittini on 2014-07-17
> **stevecarter26 said:**
> My router is probably going to stop me from doing that as it only supports a single subnet. I understand what you mean but don't know how well that would work for me.


What about? Setting metric 10 on p1p1 and metric 20 on em1 then removing the gateway IP from p1p1.
Would that only give p1p1 LAN access as no external gateway and em1 would retain it's gateway giving it external access?
Honestly, I don't quit get your network, I would appreciate a network diagram to answer your question
But I have a better idea
I don't know if any of your adapters can support to be a software AP
That would allow you to operate the WiFi adapter as a router, let's say that's Adapter 1
Adapter 1 can be used for internal file sharing and other devices can connect to this network, you can set its default gateway to be Adapter's 2 IP address
Adapter 2 can be used for whatever download you want
In that case, all your internal activity will be done over Adapter's 1 network
and when hosts connected to this network need to access the internet, their packet's will be forwarded to Adapter 2
But make sure that you are using different WiFi channels for the two adapters

---

### Post by stevecarter26 on 2014-07-17
I'll try and word this but appreciate a diagram may be better. I want the intel p1p1 adapter to be used solely for LAN transfer through SAMBA and then the onboard em1 to be used for everything else. These are both wired ethernet connections, my reason for doing this is I am conscious that I have a RAID setup on my file server so can saturate a gigabit connection so want to ensure I have a "separate route" for any traffic that isn't fileshares (ie mumble server).

192.168.1.3>p1p1>LAN file shares
192.168.1.2>em1>torents, plex, mumble, webmin

To spin this upside down, I suppose I could try and force samba into using p1p1 and leave em1 as the "default" interface?

---

### Post by stevecarter26 on 2014-07-17
If I change this in SAMBA

```
#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

```

to

```
#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 192.168.1.3/24 p1p1

```

I *think* that should force SAMBA onto the interface I want whilst leaving the em1 as the "main" interrface for other non-SAMBA traffic.

---

### Post by h.hittini on 2014-07-17
> **stevecarter26 said:**
> If I change this in SAMBA

```
#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

```

to

```
#### Networking ####


# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 192.168.1.3/24 p1p1

```

I *think* that should force SAMBA onto the interface I want whilst leaving the em1 as the "main" interrface for other non-SAMBA traffic.

I don't have experience with SAMBA or any of the things you are running, there might be a way. And get used to something, don't say you think it will force whatever, check the documentation

But form networking point of view you can do the following:
1) Connect p1p1 interface to the WAN interface on your router and configure the router's default gateway to be p1p1 IP address
2) Connect em1 interface to the cable you are getting from your ISP
3) Set the default gateway on your server for p1p1 interface to be em1 IP address
This should do the trick, but your server's security becomes a concern now, you'll need to run a firewall, despite the fact that I don't believe the router is doing that for you

---

### Post by stevecarter26 on 2014-07-17
I've added a very basic diagram as an attachment, I think it should show up for you, hopefully it makes things clearer.

---

### Post by h.hittini on 2014-07-17
> **stevecarter26 said:**
> I've added a very basic diagram as an attachment, I think it should show up for you, hopefully it makes things clearer.

Okay, this looks better now
So, just to make sure I have the whole picture, you have the following:
1) A switch connecting your LAN devices
2) A wireless connection between the server and the switch
3) A wireless connection between the server and the router
4) [COLOR=#ff0000]What type of connection between the switch and the router? Is there a connection at all?[/COLOR]
And what you want to do is to direct all the external activity from the server over em1
And you don't care about the external traffic originating from your LAN devices
Did I get everything right?

---

### Post by capscrew on 2014-07-17
> **stevecarter26 said:**
> I've added a very basic diagram as an attachment, I think it should show up for you, hopefully it makes things clearer.
You should not have 2 interfaces with the same subnet on any host (computer).  One interface will always be disabled.  This is normal.  If you look at your diagram you will note that there are 2 routes to connect to the HP server.  This is a loop that can't exist.  

If you want the HP server to have a separate subnet for certain tasks then you will have to set that up.  This would then make the HP server a router serving the 2 subnets, as it would have a separate interface in each subnet.

---

### Post by stevecarter26 on 2014-07-17
> **h.hittini said:**
> Okay, this looks better now
So, just to make sure I have the whole picture, you have the following:
1) A switch connecting your LAN devices
2) A wireless connection between the server and the switch
3) A wireless connection between the server and the router
4) [COLOR=#ff0000]What type of connection between the switch and the router? Is there a connection at all?[/COLOR]
And what you want to do is to direct all the external activity from the server over em1
And you don't care about the external traffic originating from your LAN devices
Did I get everything right?

1)Yes switch(es) connect lan devices, the diagram is very scaled down, the router has built in wireless with multiple clients but this shouldn't make any odds for this purpose currently.
2)Server to switch is cabled
3)Server to router is cabled
4)Switch to router is cabled
Yes all external traffic (inbound or outbound) I would like over em1
All internal traffic (inbound and outbound) I would like over p1p1

All other LAN devices need to carry on working through the router as a basic setup. (Should have mentioned this all sits behind NAT and routers built in firewall)

> **capscrew said:**
> You should not have 2 interfaces with the same subnet on any host (computer).  One interface will always be disabled.  This is normal.  If you look at your diagram you will note that there are 2 routes to connect to the HP server.  This is a loop that can't exist.  
If you want the HP server to have a separate subnet for certain tasks then you will have to set that up.  This would then make the HP server a router serving the 2 subnets, as it would have a separate interface in each subnet.

Dammit I really wanted to avoid this, purely for the reason this would make the remaining LAN setup very convoluted. I was hoping to push certain traffic down 1 adapter and certain traffic down another.

---

### Post by capscrew on 2014-07-17
> **stevecarter26 said:**
> ...

Dammit I really wanted to avoid this, purely for the reason this would make the remaining LAN setup very convoluted. I was hoping to push certain traffic down 1 adapter and certain traffic down another.

Read up on Ethernet and Spanning Tree Protocol.  The protocols will not allow it no matter how much you want to do it.  Back to the drawing board.  :-(

---

### Post by sedawk on 2014-07-17
For the incoming traffic the situation is clear: when you talk to 192.168.1.3, then all traffic should be directed to p1p1 and not em1.
But outgoing traffic can use em1 or p1p1. The first time your server wants to talk to another local machine on the same subnet  it sends an
ARP-request ("Who is 192.168.1.x") and  it might get the answer via em1 or p1p1 and the winner is selected for outgoing traffic.
You can see the active ARP-table with command "arp -a". 
You can remove and add entries to the arp table manually. That way you can force your server to use p1p1 when replying to a local PCs.

Setting up two subnets might be a better solution but then you might have to bother about local routing inside your net ...

---

### Post by capscrew on 2014-07-17
> **sedawk said:**
> For the incoming traffic the situation is clear: when you talk to 192.168.1.3, then all traffic should be directed to p1p1 and not em1.
But outgoing traffic can use em1 or p1p1. The first time your server wants to talk to another local machine on the same subnet  it sends an
ARP-request ("Who is 192.168.1.x") and  it might get the answer via em1 or p1p1 and the winner is selected for outgoing traffic.
You can see the active ARP-table with command "arp -a". 
You can remove and add entries to the arp table manually. That way you can force your server to use p1p1 when replying to a local PCs.

Setting up two subnets might be a better solution but then you might have to bother about local routing inside your net ...
The problem is not the destination but rather the devices the packets flow through (i.e. there are multiple paths to the destination).  All the switches will have the info needed for the destination (be it outbound or inbound for the LAN).  The router device has a switch in it also.  Spanning Tree Protocol (STP) will kick in an shut down all but one path through a single LAN.  This is to prevent loops.

So,  "Who is 192.168.1.x" is not really the problem.  It's "Which way do I go to get to 192.168.1.x".  Ethernet and STP make so that the answer is a singular path to the destination by monitoring the situation and killing the duplicate paths.  Look at the diagram again to see the duplicate paths (looping).

---

### Post by h.hittini on 2014-07-17
If I were you I would create two networks
LAN1: For file sharing, keep em1 as it is and connect p1p1 to a new router so that devices can access it
LAN2: For internet access, a connection between the router and swithces
You need to block the access between LAN1 and LAN2 and those who are connected to LAN1 can still access the internet, but it's gonna be slower because of the file sharing traffic
You can use VLANs instead of extra router and connect LAN1 to the switch, that depends on who is going to use it and how big your network is
If you used VLANs some switch ports will belong to LAN1 whereas others will belong to LAN2, if you decided to go with a new router you should remove the connection between p1p1 and the switch

---

### Post by stevecarter26 on 2014-07-17
> **capscrew said:**
> You should not have 2 interfaces with the same subnet on any host (computer).  One interface will always be disabled.  This is normal.  If you look at your diagram you will note that there are 2 routes to connect to the HP server.  This is a loop that can't exist.  

If you want the HP server to have a separate subnet for certain tasks then you will have to set that up.  This would then make the HP server a router serving the 2 subnets, as it would have a separate interface in each subnet.

I think I understand what you mean, in short I don't want to go down the line of making the server a router but I suppose I could add a router between it and the router, this router could then hand off a different IP range and would be a different gateway, wan traffic could then go to that and in whilst leaving the LAN interface.

Thats food for thought then, alternatively I could look at a different router that can hand off multiple subnets (Draytek 2830 as I at least know a bit about them).

Thanks guys, for the time being I may just shove everything over onto the strongest (p1p1) interface and see what I can do. You've all been a really great help!

---

### Post by capscrew on 2014-07-17
> **stevecarter26 said:**
> ... I suppose I could add a router between it and the router, this router could then hand off a different IP range and would be a different gateway, wan traffic could then go to that and in whilst leaving the LAN interface.

The downstream router would have it's WAN interface connected to an upstream ethernet LAN interface.  IN this way the Internet is always through the original router.  If you have 2 wan interfaces ( and 2 ISP connections) you are talking about much more complication than you need to endure.  VLANs are another thing all together.  You need to have a managed switch that will allow VLAN conffigureation.> 


Thats food for thought then, alternatively I could look at a different router that can hand off multiple subnets (Draytek 2830 as I at least know a bit about them).

I don't know of any residential gateway (home router) that will support 2 subnets.  I'm not say that there isn't one, just that it would be a rare thing to find.  Check carefully. 
> 

Thanks guys, for the time being I may just shove everything over onto the strongest (p1p1) interface and see what I can do. You've all been a really great help!
if we are done here then mark this thread [SOLVED]!!!  You can do that using the appropriate drop down menu that is at the top of this page.

---

