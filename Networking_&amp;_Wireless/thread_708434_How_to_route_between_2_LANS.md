---
title: "How to route between 2 LANS"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by fantafe on 2008-02-26
Here is my situation, I have Ubuntu Box with 3 NICs as descriped below:

-> eth0 (connected to ISP with a public IP)
-> eth1 (connected to LAN1 172.16.0.0/17)
-> eth2 (connected to LAN2 172.16.128.0/17)

I have dhcpd, DNS and BIND installed on Ubuntu box everything is functioning as intended but my problem is hosts on LAN1 can't reach LAN2 and vise versa. I know this is a routing issue.

Here is the output for /etc/network/interfaces

```

auto lo eth0 eth1 eth2
iface lo inet loopback
iface eth0 inet dhcp

iface eth1 inet static
        address 172.16.1.1
        netmask 255.255.128.0
        broadcast 172.16.127.255
        network 172.16.0.0

iface eth2 inet static
        address 172.16.129.1
        netmask 255.255.128.0
        broadcast 172.16.255.255
        network 172.16.128.0

```

and this is the output of my route -n

```

Destination	Gateway		Genmask		Flags	Metric	Ref	Use	Iface
172.16.128.0	0.0.0.0		255.255.128.0	U	0	0	0	eth2
172.16.0.0	0.0.0.0		255.255.128.0	U	0	0	0	eth1
62.0.0.0		0.0.0.0		255.0.0.0		U	0	0	0	eth0
0.0.0.0		62.151.234.43	0.0.0.0		UG	0	0	0	eth0

```

What am I missing? can anyone tell me what am I doin wrong?

---

### Post by SpaceTeddy on 2008-02-26
> sudo su
echo 1 > /proc/sys/net/ipv4/ip_forward
or use
> sudo pico /etc/sysctl.conf
and uncomment this line
> net.ipv4.conf.default.forwarding=1

both enable ip forwarding

---

### Post by fantafe on 2008-02-27
I have IP forwarding enabled and my iptables have no restrictions in the forwarding chain. Can you think of any other reasons why it's not working?

---

### Post by SpaceTeddy on 2008-02-27
only other reason would be that your client in each lan do not know where to search for the other one - i.e. they are missing their routes to the other network... 

i don't know what kind of machines you have there, but it is possible that you give me a printout from one of the clients routing table in one of the lans ?

---

### Post by Mr. C. on 2008-02-27
Make sure any system on the:
[LIST]
[*]172.16.0.0 network has its default route set to 172.16.1.1
[*]172.16.128.0 network has its  default route set to 172.16.129.1
[/LIST]

MrC

---

### Post by SpaceTeddy on 2008-02-27
> **Mr. C. said:**
> Make sure any system on the:
[LIST]
[*]172.16.0.0 network has its default route set to 172.16.1.1
[*]172.16.128.0 network has its  default route set to 172.16.129.1
[/LIST]

MrC

I would strongly **advice against setting the default route**. this will most likely mean that you loose internet connection in both lans... just add a normal route for each of the hosts without touching the default one.
(unless your router is also the machine that connects everything to the internet... but then it should work without the routes in the clients...)

---

### Post by Mr. C. on 2008-02-27
> **SpaceTeddy said:**
> I would strongly **advice against setting the default route**. this will most likely mean that you loose internet connection in both lans... just add a normal route for each of the hosts without touching the default one.
(unless your router is also the machine that connects everything to the internet... but then it should work without the routes in the clients...)

There is no probability involved here.  The default route must be correct.  I didn't say the OP would need to change it - I said to ensure it was *correct*.

All hosts need the route for the network connected to the attached interface, and the default for everything else.

MrC

---

### Post by SpaceTeddy on 2008-02-27
It does not help anybody if we argue about semantics here.
Lets stick to fixing the problem instead of getting hung up over something that was misinterpreted.

---

### Post by Mr. C. on 2008-02-27
> **SpaceTeddy said:**
> It does not help anybody if we argue about semantics here.
Lets stick to fixing the problem instead of getting hung up over something that was misinterpreted.

I agree.  And neither of your posts have offered any problem resolution or assistance.

---

### Post by Mr. C. on 2008-02-27
fantafe,

Please clarify for us.  Are your 172.16.0.0/17 and 172.16.128.0/17 networks each connected to an their own routers ?  Or is the Ubuntu box acting as the Internet router for those networks?

If the former is the case, then you need to add static routes to each host on on those two LANs which tells those hosts how to reach the other network.

If the latter is the case, then my earlier request to check the default routes stands.

If there is some other setup, please clarify.

MrC

---

### Post by fantafe on 2008-02-27
Thanks guys for your time and the input. To clarify the situation. All the hosts on both subnets are windows hosts. and yes the Ubunbu Server Box is providing internet for both subnets and the NATing is working fine both subnets have internet access and both subnet have the correct default gate way:
 
subnet 172.16.0.0/17      has gateway 172.16.1.1
subnet 172.16.128.0/17  has gateway 172.16.129.1

This is all configuered in the dhcp server so client in both subnets get the correct ip information. The strange part is. I still cannot figue out why i cant ping host from 172.16.0.0/17 to a host in 172.16.128.0/17 do I have to create additional static route in the Ubuntu Box to route between the teo subnets?

here is the output of route print from a host on 172.16.0.0/17
```
C:\WINDOWS>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 11 11 eb 7b d0 ...... Broadcom NetXtreme 57xx Gigabit Controller - Packet Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0       172.16.1.1      172.16.5.1       10
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
       172.16.0.0    255.255.128.0       172.16.5.1      172.16.5.1       10
       172.16.5.1  255.255.255.255        127.0.0.1       127.0.0.1       10
   172.16.255.255  255.255.255.255       172.16.5.1      172.16.5.1       10
        224.0.0.0        240.0.0.0       172.16.5.1      172.16.5.1       10
  255.255.255.255  255.255.255.255       172.16.5.1      172.16.5.1       1
Default Gateway:        172.16.1.1
===========================================================================
Persistent Routes:
  None
```

and this is the output from a host on 172.16.128.0/17

```
C:\WINDOWS>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 16 6f 0e 42 49 ...... Intel(R) PRO/Wireless 2200BG Network Connection - Packet Scheduler Miniport
0x3 ...00 13 a9 0b c9 bf ...... Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller - Packet Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0     172.16.129.1  172.16.255.251       25
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
     172.16.128.0    255.255.128.0   172.16.255.251  172.16.255.251       25
   172.16.255.251  255.255.255.255        127.0.0.1       127.0.0.1       25
   172.16.255.255  255.255.255.255   172.16.255.251  172.16.255.251       25
        224.0.0.0        240.0.0.0   172.16.255.251  172.16.255.251       25
  255.255.255.255  255.255.255.255   172.16.255.251               3       1
  255.255.255.255  255.255.255.255   172.16.255.251  172.16.255.251       1
Default Gateway:      172.16.129.1
===========================================================================
Persistent Routes:
  None
```

So settings look pretty fine for me! any other input please

---

### Post by Mr. C. on 2008-02-27
This route in the first sytem's table does not look correct:
```

Network Destination        Netmask          Gateway       Interface  Metric
...
172.16.255.255  255.255.255.255       172.16.5.1      172.16.5.1       10
```

Th 172.16.5.0 network has a valid CIDR range of 172.16.0.0 to 172.16.127.255 (the last being the broadcast address).  Windows creates a local, interface-specific broadcast route, which should look like:
```

172.16.127.255  255.255.255.255       172.16.5.1      172.16.5.1       10
```
This seems to indicate your have something wrong on your network config on this host.  Although you use DHCP, perform a specific test using static IP's on these host (and the second host show in the table above).  Be sure to set the netmask is correctly set on both systems.

And I'm not sure what this route is in the second table:

```
Network Destination        Netmask          Gateway       Interface  Metric
255.255.255.255  255.255.255.255   172.16.255.251               3       1
```

What is interface "3" ?

Be sure your DHCP server that is proving configuration information for both LANs is configured correctly (it should have two LAN-specific **subnet** statements, each with correct information)

You do not need to create any additional or static routes on these hosts, since they are using your Ubuntu box as the gateway.  Each host knows how to reach its own network, and for everything else, packets are passed to the default route (whicih is the Ubuntu box, which knows how to reach both pf the private LAN networks and of course everything else via its WAN interface gatewaying to the router.

MrC

---

### Post by fantafe on 2008-02-28
MrC you are right about the first host routing table has incorrect broadcast route i guess i missed that. that routing table was windows generated. I don't know if this is a bug in windows . but I'll try and set the ip to static and see how that routing table get generated.
by the way interface 3 is just unconnected NIC that host has 2 NICs. Let me do the static IP test tonight and I'll get back with the results

---

### Post by fantafe on 2008-03-01
Apperently Windows dhcp client does not create the correct broadcast route for the non standard subnets mask my understanding that the standard subnet masks as the following:

Class A Network 255.0.0.0
Class B Network 255.255.0.0
Class C Network 255.255.255.0

and since my network is class B so windows dhcp client assume that i'm using the 255.255.0.0 mask and therfore creates the route accordingly. I would concider this is a bug in windows dhcp client. so the lesson learned is to stick to standards to avoid bugs. 

I changed my 2 subnets to 172.16.0.0/16 and 172.17.0.0/16 and the routeing tables was created fine by the windows host and now i can reach hosts from both sides.
I just like to thank Mr. C.  and SpaceTeddy for thier input

---

### Post by Mr. C. on 2008-03-01
Excellent!

FYI: You were not using a Class B - you were using CIDR which breaks the old class rules.  Class B is 16 bits network. (/16, not /17).

See: Week 6: Networking Basics, Page 9:  [http://cis68c1.mikecappella.com/](http://cis68c1.mikecappella.com/)

MrC

---

