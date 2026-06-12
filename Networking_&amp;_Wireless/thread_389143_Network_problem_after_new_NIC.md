---
title: "Network problem after new NIC"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2007-03-20
Ugh! I installed a  new Gigabit NIC with Realtek chip. It was found as eth1. Now Boot up is taking long & I have to do ctrl-c, In Network manager deactive & activate and Internet starts working. I have in /etc/network/interfaces:

auto eth1
iface eth1 inet dhcp

auto eth1:1
iface eth1:1 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

Why it hangs during boot? It worked When I had eth0 (10Mb).

---

### Post by netztier on 2007-03-20
> **cd-r80 said:**
> Ugh! I installed a  new Gigabit NIC with Realtek chip. It was found as eth1. Now Boot up is taking long & I have to do ctrl-c, In Network manager deactive & activate and Internet starts working. I have in /etc/network/interfaces:

```
auto eth1
iface eth1 inet dhcp

auto eth1:1
iface eth1:1 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

Why it hangs during boot? It worked When I had eth0 (10Mb).


Huh? this looks weird :confused: 

*First thing:* clear out **/etc/iftab** or change it to assign eth0 to your new NIC's MAC address. If you have multiple interfaces in your box, edit /etc/iftab to assign ethX to the NICs the way you want it.

*Second thing:* is there a particular reason to create a subinterface **eth1:1** with a static IP address, while the main interface **eth1** still has DHCP? 

[INDENT][SIZE="1"]Come to think of it.. Did you enable "Internet connection sharing", i.e. with firestarter or iptables? This looks like a horrible configuration result, with mixed-up internal and external interfaces *eeeew*.
[/SIZE][/INDENT]

I suggest you change /etc/network/interfaces to one of the following variants (assuming that your new card now has eth0). This should get you started at least. Setting up Internet sharing and the like will come later...


If there is a some DHCP service available to you (either from your ISP or from your broadband router)
```
auto eth0
iface eth0 inet dhcp

```


Or (assuming that you actually need 192.168.0.1 /24 on that interface):
```
auto eth0
iface eth0 inet static
 address 192.168.0.1
 netmask 255.255.255.0
 broadcast 192.168.0.255
 gateway 192.168.0.1

```


best regards

Marc

---

### Post by cd-r80 on 2007-03-20
Thanks I had forgot that /etc/iftab (too tired...). I removed old eth0 & it was still in /etc/iftab &  new was assigned as eth1. No I don't use Connection Sharing. Virtual IP is for my fileserver. New Nic then did not appear automatically after install in /etc/iftab...ok.

---

### Post by cd-r80 on 2007-03-21
Huh! I rebooted and it was not enough /etc/iftab. Now I still have to start networking manually, at boot it hangs? What I'm still missing?

---

### Post by chili555 on 2007-03-21
What does /etc/network/interfaces look like now?

In my opinion, this will probably never work:```
address **192.168.0.1**
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway **192.168.0.1**
```

I don't believe the gateway is going to let you connect with it's *own* address.

---

### Post by stchman on 2007-03-21
> **cd-r80 said:**
> Ugh! I installed a  new Gigabit NIC with Realtek chip. It was found as eth1. Now Boot up is taking long & I have to do ctrl-c, In Network manager deactive & activate and Internet starts working. I have in /etc/network/interfaces:

auto eth1
iface eth1 inet dhcp

auto eth1:1
iface eth1:1 inet static
address 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

Why it hangs during boot? It worked When I had eth0 (10Mb).

Your IP address should be something like 192.168.0.105 or something around there.

Also change your hosts and hostname files to one liners.

/etc/hosts
127.0.0.1 localhost bob-laptop

/etc/hostname
bob-laptop

replace bob-laptop with your host name of course.

Hope this helps.

---

### Post by cd-r80 on 2007-03-21
Gateway 192.168.0.1 does not seem to bother. It is only LAN. This conf- worked well before NIC change. /etc/init.d/network restart everything works, but not at boot? Router is 192.168.0.254 no conflicts.

Something to read:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

---

### Post by Mr. C. on 2007-03-21
I can't interpret your "does not seem to bother" response, but let me be more forceful about something stated earlier.

Your IP address of 192.168.0.1 is wrong, or your gateway is wrong.  They cannot both be the same.  You are confused about IP addresses.  You must pick an IP address unused by any other piece of Ethernet hardware on your network.

MrC

---

### Post by netztier on 2007-03-22
> **cd-r80 said:**
> Gateway 192.168.0.1 does not seem to bother. It is only LAN. This conf- worked well before NIC change. /etc/init.d/network restart everything works, but not at boot? Router is 192.168.0.254 no conflicts.

No conflicts? I bet there are. 

If that router has 192.168.0.254, it very probably also runs a DHCP service that will dole out addresses from the 192.168.0.xxx range. Along with that information will come what is called the "DHCP Options", and they contain information about the default gateway, the subnet mask, and the DNS servers (there may be more, but that's the basic set that is really needed).

Probability that the router's DHCP service will advertise it's own IP address as default gateway is very high, since that's what most routers do. Check the routing table's content with **netstat -nr** or **route**.

So now we can assume that your **eth0** which is configured for DHCP has an address somewhere in the 192.168.0.xxx range, and it has learnt via DHCP what the correct default gateway is - if my assumptions are right, it's default gateway is 192.168.0.254.

Adding a secondary (virtual) IP address (sometimes called an IP alias) to that interface is legitimate - even choosing the .1 as address, when the router is at .254. However it is not correct to configure a separate "gateway" for that sub-interface in /etc/network/interfaces, and even more so to make the "gateway" statement the same address as the interface itself. [COLOR="Blue"]Remove the marked line below to avoid routing table confusion[/COLOR], and compare the routing table before and after the change.

```
auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
[COLOR="Red"]gateway 192.168.0.1[/COLOR]

```


Per IP stack and thus per routing table, you can have only one active default route at any given time. There may be more than one entries for the destination network 0.0.0.0, but it's a "first match" thing. If there are multiple interfaces, the one to come up last will enforce it's default route over the other(s). So you never really know which one will be active.

Besides - what would you actually need a second address on the same interface for? If there are clients in your LAN that are to connect to your server, they can do that just as well with the primary interface's address that is something like 192.168.0.xxx. If you worry about a changing IP address because of DHCP, simply configure the router's DHCP server to give out a "static lease" to the MAC address of your server's primary NIC - or configure eth0 with a static IP address altogether. That would then look something like this:

```
auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.254

```

Before activating this change, look at the contents of **/etc/resolv.conf** and take a copy of it, while eth0 still runs in DHCP mode. With DHCP deactivated, your system won't learn about DNS servers, so you'll have to configure them manually. Creating/restoring **/etc/resolv.conf** from what it looked like "in it's DHCP days" will do this.

Real benefits of secondary addresses can come in if you want to address security concerns, for example in that you want to make sure that some service doesn't listen on one (sub)interface or IP address, but on a specific one. In that case you have to make sure that you configure the services (Samba, Apache, etc.) to listen only to the (sub)interface you actually want them to.


best regards

Marc

---

### Post by cd-r80 on 2007-03-22
Thank you very much! I did not know that subinterface cannot have gateway or so... Now my NET works. No, I don't have DHCP On a router. The router is same time a hub for LAN and a bridge to internet. No it works well like before. I donnou when I started to put that gateway... Yes Eth0 is DHCP, but from ISP.

---

### Post by netztier on 2007-03-22
> **cd-r80 said:**
> The router is same time a hub for LAN and a bridge to internet. No it works well like before. I donnou when I started to put that gateway... Yes Eth0 is DHCP, but from ISP.

Hm. It's a good thing that this setup now works. With the way you use the terms hub, bridge and router however, I get more and more confused - since I have a completely different approach to them - one I learnt in Cisco courses and used in certificate tests.

The way I use the terms is this:

**Repeaters** and Multiport Repeaters (aka **Hubs**) are "stupid" devices that work at ISO/OSI Layer1. They just "repeat" the Ethernet signals, they are unaware of MAC addresses or IP addresses. A signal entering a Hub port will be replicated to all the others, therefore all connected devices share the 10 or 100Mbps bandwith. Real Hubs are an endangered species and you'll have a hard time finding new ones these days, and you probably won't find any more of them that are manageable and have IP addresses for that purpose.

A **Bridge** or a multiport Bridge (aka **Switch**) are more intelligent. They work at ISO/OSI Layer 2 and are able to learn MAC addresses as Ethernet frames are travelling through them. They internally populate and use a lookup table that matches MAC addresses to ports. A frame entering a port will be forwarded only to the port where the destination MAC address is known to be. A good switch can support full ethernet speed (10, 100 or 1000Mbps) "any-to-any" across it's internal backplane. A switch however is unaware to IP-adresses. Higher class, so-called "managed switches" have one IP address which will allow to connect to them for configuration of Ethernet parameters, but for it's basic function, it doesn't need an IP address.

A **Router** now is more advanced. It knows about IP addresses, each of it's interfaces has one. Internally, a router works with a **routing table**, to look up out of which interface it has to send a packet for a certain destination IP address. 

A router is absolutely needed if you want to communicate from one IP subnet to another, for example a PC in 192.168.4.0 /24 needs to ssh into a server in 192.168.10.0 /24. There has to be a router with two interfaces, one each in the switch/hub that carries the LAN with 192.168.4.0 and the switch/hub that carries the LAN with 192.168.10.0.

Routers also can have built-in DHCP servers that can dole out addresses for the subnet(s) they are connected to - and they can even be DHCP clients, to obtain an IP address for some of their interfaces.

Now your common Broadband Router or Wireless Router is built like this:

[LIST]
[*] one external Ethernet interface, sometimes also called "WAN Ethernet". It runs a *DHCP client* on that NIC to get an address from the ISP. That's where you connect the xDSL or cable modem.
[*] one internal Ethernet interface, without an outlet, but an internal connection to the integrated 4-port switch. It has a static IP address (commonly 192.168.0.1) and runs a DHCP *server* on that interface.
[*] an integrated 4-port switch, that has a 5th internal port to the router, and sometimes a 6th internal port that connects to the integrated Wireless Access Point. 
[/LIST]

With all computers connected to the wireless AP or the internal 4-port switch, no computer will ever obtain an address from the ISP, but all are in 192.168.0.x, and all can talk to each other easily. Whenever they want to send an IP packet to the internet, they just send it to the router, which thus takes the role of their "**default gateway**".

I'd like to understand your network setup - can you give me a bit more details? ISP connection, DHCP clients and servers, Subnet addresses and also how hub, router and computers are cabled to each other?

best regards

Marc

---

### Post by cd-r80 on 2007-03-22
OK! I wrote & asked about this in "servers & security" some time ago. Here is my network: NO NAT.

Damn Small Linux Fileserver
eth0: DHCP IP from ISP
eth0:1: 192.168.0.2
|
|
|
Telewell ADSL Modem
4 ports
Bridge mode ON          -------------512Kb------------ISP 5 IPs available.
LAN IP 192.168.0.254
DHCP server OFF
|
|
Xubuntu Dapper Workstation
eth0: DHCP IP from ISP
eth0:1 192.168.0.1

I use SFTP to  move files from,to a fileserver. "Accidentally" I noticed that My ADSL "box" works same time as a LAN & "Bridge from ISP". Now I have used only one NIC in each machine. I have no problem surf in internet & same time move files to a fileserver.  Perhaps it slows a little bit, but very little.

---

### Post by netztier on 2007-03-23
> **cd-r80 said:**
> 
Damn Small Linux Fileserver
eth0: DHCP IP from ISP
eth0:1: 192.168.0.2
|
|
|
Telewell ADSL Modem
4 ports
Bridge mode ON          -------------512Kb------------ISP 5 IPs available.
LAN IP 192.168.0.254
DHCP server OFF
|
|
Xubuntu Dapper Workstation
eth0: DHCP IP from ISP
eth0:1 192.168.0.1



Ok, now I understand a lot better, thanks! What you have there is sometimes called a "Multinet": more than one IP subnet on a single underlying broadcast domain. In that regard, having a second IP address on the systems makes sense. Just make sure that you have a local name resolution mechanism that returns the other device's 192.168.0.x address, not the ISP-assigned one. Like this you can be sure that the traffic stays local to your LAN and never has to cross the bridge and come back. Can you verify it the ISP-assigned addresses are always from the same subnet?

I can spot a possible downside in such a setup: depending on the configuration of the bridge function, broadcast and multicast packets from your secondary LAN interface may leak out to your ISPs network. Should you be using multicast streaming (i.e for video or audio) within that LAN, the possibly large data stream (multiple Megabits/s) could be bridged out to the ISPs network. This would certainly exceed the upstream capacity of your DSL connection by an order of magnitude, and in consequence your dowload rates would be crippled.

The other downside possibly is that you get to see all broadcast traffic (especially ARP-probing) from your ISP's network segment on your internal LAN. I for myself would want these things dealt with (i.e. dropped) at the gate, not in my garden. That's why I always want a router at my network boundaries, but YMMV.

best regards

Marc

---

### Post by Mr. C. on 2007-03-23
netztier - multinet is not a term I'm familiar with, and the concept of "subnet" (which is defined as two or more distinct networks separated by routers) implies different broadcast domains, not the same.

Its not at all clear to me why the OP doesn't not placing a NATing router/switch combo after the modem, and maintain privacy and simple setup.  The use of 192.168.0.[12] are not in the OPs control of the ISP managed the subnet 192.168.0.0/24.  The OP may only use the 5 IPs assigned to him, and may be usurpping someone else's IP (elsewhere on that subnet).

MrC

---

### Post by cd-r80 on 2007-03-23
ISP Net & eth0s are  84.x.x.x Real World IPs. That's why not NAT.  Nothing to do with LAN part 192.168.0.0. It never makes route via ISP net when I connect 192.168.0.2 for example.

---

### Post by Mr. C. on 2007-03-23
I can't understand a word you are saying.

If you want help, you're going to have to be much more clear, precise and articulate than you have been.  Your statements and conclusions simply make no sense.

Until then, not much I can help you with.
MrC

---

### Post by cd-r80 on 2007-03-24
Well. like I said already thanks before. There is no problems. It was only that eth0:1 gateway & old /etc/iftab which made problems. I don't know how it could be more clear than my network diagram shows? Everything works fine. Here again with a little bit more 

Damn Small Linux Fileserver
eth0: DHCP IP from ISP. Real world IP like for ex. 66.66.66.66
eth0:1: 192.168.0.2 static
|
|
|
Telewell ADSL Modem
4 ports
Bridge mode ON -------- WAN-----512Kb------------ISP 5 IPs available.
LAN IP 192.168.0.254
DHCP server OFF
|
|
Xubuntu Dapper Workstation
eth0: DHCP IP from ISP . Real world IP 66.66.55.55
eth0:1 192.168.0.1 static

---

### Post by netztier on 2007-03-24
> **Mr. C. said:**
> netztier - multinet is not a term I'm familiar with, and the concept of "subnet" (which is defined as two or more distinct networks separated by routers) implies different broadcast domains, not the same.

"As by the books", one does not run multiple IP subnets on a single broadcast domain, but IMHO there's no rule that forbids it. You **can** have each a set of hosts in 172.16.1.0/24 and 172.16.2.0/24 on the same LAN or (V)LAN (i.e broadcast domain). Not that it's a good thing to do, but it's possible. I've learnt that this is called a "multinet". 

Such a thing has of course it's downsides, such as that every system gets to see the sum of all broadcast traffic, also from the other IP subnets. In small environments, this does not hurt, but as soon as things get advanced, such as multicast coming into play, things get ugly, and it's not something you do if network security is a concern.

The other downside is that you need a router if you want to connect from one IP range to the other, and that router will have to be a "router on a stick" with a primary and secondary address. Another ugly thing.

> **Mr. C. said:**
> 
Its not at all clear to me why the OP doesn't not placing a NATing router/switch combo after the modem, and maintain privacy and simple setup.  The use of 192.168.0.[12] are not in the OPs control of the ISP managed the subnet 192.168.0.0/24.  The OP may only use the 5 IPs assigned to him, and may be usurpping someone else's IP (elsewhere on that subnet).

From how I understand it, the OP's systems get a "public" IP address via DHCP, and have a static "private" IP on the first subinterface to communicate with each other. Now why the OP wants to expose his systems unNATted to the Internet is his own choice. It can have it's advantages if you want to run some services that have trouble with NAT etc.

The other thing is that most broadband routers can only pull one DHCP lease on the external interface. But what if you'd like to use all 5 public IPs you are actually paying for? Running up to 5 routers doesn't make more sense, either. I think you could do it with an advanced router, but not with the SOHO class devices you can buy for a few dozen (more) of bucks.

best regards

Marc

---

