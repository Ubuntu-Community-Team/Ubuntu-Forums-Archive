---
title: "Multiple NICs"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by pjhsv on 2007-03-07
Hey, i'm having some problems with 2 NICs in my new Ubuntu installation...

They are both detected by Ubuntu perfectly, and they are both perfectly working, the problems i'm having, however, are with IP addressing and routing.  Here's my setup.

eth0 - static IP address, routes all of my traffic

eth1 - is only occasionally connected, when it is, it needs to get an IP address via DHCP from whatever device I connect it to.

eth0 works fine, but as soon as I plug eth1 in, firstly, I can't seem to get a DHCP address, and secondly, it keeps changing my /etc/resolv.conf, which means eth0 can't connect to my DNS.  once I change /etc/resolv.conf back to what it should be, all works fine.

my /etc/network/interfaces is

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 202.x.x.x
netmask 255.255.255.224
gateway 202.x.x.x


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1

This was all auto-generated, I haven't added anything in there.

What I need, essentially, is to have eth0 do everything for me, with its static IP address, and then be able to plug eth1 into a router/switch/something with a DHCP server on it, and communicate with the DHCP device, (presumably it would have 192.168.0.1, 10.0.0.1 etc.etc depending on the DHCP server), but still leave my main DNS as 202.x.x.1 & 202.x.x.2 for my eth0 card.

My only problem is, i'm trying my best to convince everyone in my office to change to linux (or more to the point, to change away from MS & MacOS), but this is something that is so easy to configure in windows its not funny (set metric priorities, and everything else works)

Hope this makes sense. Thanks for the help.

---

### Post by Mr. C. on 2007-03-07
Have you configured your DHCP servers on all your other devices to hand out addresses that are known to your dual-nic'd server ?

What is the purpose of having your eth1 be a dynamic IP ?

If you want your server to route, both eth0 and eth1 should have static IPs.  Let your server hand out IPs but running a DHCP server on it.

Don't use auto if you don't want the things changed from under you.

If you want more help here, show output from 

ifconfig -a

when both interfaces are up.

MrC

---

### Post by pjhsv on 2007-03-07
The reason I need to do it, is that eth0 is my primary card, but I sometimes need to configure ADSL routers or switches, but I can't connect them to my LAN.  The reason it needs to be dynamic, certain brands of routers use different IP ranges (D-Link use 10.0.0.0, Dynalink, Billion, and most others use 192.168.1.0 etc.etc, plus I occasionally need to plug in a device that is different again (for instance i'm trying to plug a device in that serves out 202.124.x.x/29 addresses).

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0A:48:1E:A9:EC  
          inet addr:202.x.x.70  Bcast:202.x.x.95  Mask:255.255.255.224
          inet6 addr: fe80::20a:48ff:fe1e:a9ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:425812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208663 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:321954333 (307.0 MiB)  TX bytes:46153295 (44.0 MiB)
          Interrupt:217 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:40:F4:3A:D4:1C  
          inet addr:192.168.5.2  Bcast:192.168.5.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:412597 (402.9 KiB)  TX bytes:249650 (243.7 KiB)
          Interrupt:58 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38208 (37.3 KiB)  TX bytes:38208 (37.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Hope that made it a bit clearer.. ?

---

### Post by pjhsv on 2007-03-07
Oh, and that 192.168.5.2 address in eth1 is a DHCP address that got assigned yesterday, but never worked.  There's nothing in /etc/network/interfaces about it, so i'm not sure why it's still there (perhaps it continues to report the last used address, until something new comes along..??)

---

### Post by Mr. C. on 2007-03-07
So here's the deal.

If you setup a system to ask for IP information, by default, you receive the following:

- IP address
- Network mask
- Gateway IP
- DNS IPs
- domain name

The gateway IP is what gets placed into the routing table, and this controls the default route.

If you bring up a new interface, the network config scripts will assign these values to the interface, because it doesn't know you want to do otherwise.  As far as it knows, this is a new connection with a higher priority, and should take precedence.

If you want to configure this way, you will have to either modify your DHCP requests or scripts to not update the gateway.  It is easy enough to do.

MrC

---

### Post by pjhsv on 2007-03-08
Can I not have different DNS servers and default gateways for each card?  I need to update the default gateway on the second card, or it wont be able to connect to whatever router I plug into it. ?

Why does it assume that a new connection would take higher precedence?  That seems pretty silly to me.  Is there a way to assign priorities to cards?

Is something like /etc/resolv.conf.eth0 and /etc/resolv.conf.eth1 possible?

---

### Post by Mr. C. on 2007-03-08
Unix/Linux has one "resolver" for the entire system.  It makes no sense to have more than one.  All programs that want to query DNS go through the resolver.  DNS is per-system, not per-interface.

Each interface has its own route entry in the routing table, to tell the system where the packet should be placed.  This causes packets destined for a given network to be placed "on that wire".

The system cannot have two *default* gateways, because by definition, "default" means: "on which wire should I place a packet, and what next hop router will receive and forward it".  This implies you cannot have multiple "default" gateways.

You can have network- or host-specific routes; configure those as static routes.  The important point is that any packet you place on the wire, must be addressed to a known receiver (router).

Its not silly for a new interface to take precedence.  Imagine you an active Ethernet connection on your laptop.  Now, you want to dial into, say, AoL.  You use your modem to do this, and establish the connection.  Before the connection, ALL of your offsite traffic was sent through to your router.  Now that the AoL connection is established, where should all unknown traffic go?  If it goes through your Ethernet interface, AoL doesn't get it.  If it goes through AoL, then it cannot go to your Ethernet.  Priority for the modem here takes precedence.  But it doesn't have to be that way - in fact, it could be the other way around.  But it cannot do both at the same time.

Ubuntu chose to let the last connection become the new default.  If you want to run your system as a router, you need to know some advanced concepts, and you should not expect to use the automatic tools designed for novices.  If you want to be a novice, don't try to do advanced things like plug-in and use two Ethernet cards at the same time.

If you want to know more about how this stuff works, read the notes for Week's 1-3, and 6 here: [http://cis68c2.mikecappella.com/calendar.php](http://cis68c2.mikecappella.com/calendar.php)

MrC

---

### Post by pjhsv on 2007-03-08
You consider putting two network cards into a PC to be advanced?

I don't need to run my system as a router at all, I never said I did.

I never mentioned anything about using "automatic tools designed for novices", the only references I actually made in the thread were to /etc/resolv.conf /etc/network/interfaces and ifconfig.  I did, however, say that it's easier to do in MS Windows (which is clearly true)

In any case, I sorted it out this morning.  It's all working fine.  I still much prefer the way MS does it (God I hate saying that...)

---

### Post by Mr. C. on 2007-03-08
You did indicate you felt it was "silly".  You did say that you used the auto-tools ("auto-generated").  And asked for why it didn't work.

But I think you've taken my explanation too personally.  It was meant to educate and explain, not assault.  My intent was to show that *a* choice has to be made; not poke fun of your choice.

As to comparisons between other platform, its all relative.  Some distros do it one way, some do it another.  Some argue that on Windows, their modem connection should not override their Ethernet connection - but it does.  It is simply a consequence of technology that is beyond most folks' understanding, and *a* choice has to me made for them.

I personally don't think multi-homed (more than one interface) is advanced, but the vast majority of users do.  They are terribly lost when it comes to DNS IPs, static/dynamic IPs, gatway IPs, routers, netmasks, packets, ISPs, "the Internet", mail servers, pop servers, and on and on.

Anyway, glad you have it all working out.
MrC

---

### Post by pjhsv on 2007-03-08
Yep, I see what you mean.  All good.  Cheers.

---

