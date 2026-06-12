---
title: "Wireless internet share with neighbor thru ubuntu"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by JustinMorris on 2007-08-18
I am going to be sharing my internet with a few of my neighbors but I want to be able to regulate ports and divvy up speed so they don't hog all of it.  You can see on the diagram how I will have it setup.  I have 'basement' on eth0 and it is connected to the network just fine.  'linksys' is on eth1.  How do I get 'eth1' to talk to 'bindford'?

Currently I have the dhcp on the 'binford' wireless router.  I imagine I would want to setup dhcp on 'basement' so that I can create the complex rules that block ports and regulate speed for my neighbor's computers and not mine based upon IP address?

Some direction would be great, thanks.

---

### Post by steveneddy on 2007-08-18
You should be able to set this on the router that your neighbor will be using to access your network.

My Linksys router can slow connections of certain ip addresses in the set up menu.

---

### Post by JustinMorris on 2007-08-18
True, but the only problem is, I get no internet on the router for some reason, I don't think the two ethX are talking?

eth0      Link encap:Ethernet  HWaddr 00:03:47:0B:6B:0F
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fe0b:6b0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8831022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20208005 errors:1 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:4010955299 (3.7 GiB)  TX bytes:3055570174 (2.8 GiB)

eth1      Link encap:Ethernet  HWaddr 00:D0:B7:B1:97:DB
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by steveneddy on 2007-08-18
The open to neighbor router goes **through** the Ubuntu server?

Are there two ethernet cards in the server?

I personally would run the cable to the second router first, make the first router a gateway, plug the server into the second router.

Or make the server the DHCP server if it has two ethernet cards.

---

### Post by JustinMorris on 2007-08-19
> The open to neighbor router goes through the Ubuntu server?

That is right, and there are two ethernet cards in the Ubuntu server.  See the diagram in the first post. I thought I would have much more control, flexibility and security if I had the neighbors traffic come through the Ubuntu machine with any appropriate software installed.

---

### Post by JustinMorris on 2007-08-19
Anyone have a solution?

---

### Post by JustinMorris on 2007-08-19
Let me try to say it a different way.  I have internet on eth0.  I want eth1 to know that eth0 has internet.    How do I get that far?  I would also like to be able to limit connections on eth1 to a certain speed and block certain ports, etc...  Maybe that will clear it up?

---

### Post by JustinMorris on 2007-08-26
Anyone?  I tried this ([http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)) and it did not work.

---

### Post by JustinMorris on 2007-09-23
I thought I could try to revive this thread, as I am still trying to figure this one out.  I have read a lot and tried many things.  If you take a look at my attachment in the first post you should get a good idea of what I wish to accomplish with the "open" wireless router going thru the ubuntu box.  Please help!

Thanks,

---

### Post by degreseven on 2007-09-23
I'm no networking expert, but I think you may need some iptables rules. I used to use a gentoo box as a router/ firewall & they have a couple great guides on the subject. I would recommend reading through this first...

[http://gentoo-wiki.com/HOWTO_Iptables_for_newbies](http://gentoo-wiki.com/HOWTO_Iptables_for_newbies)

Here is the guide I used for setting up my router. It is (obviously) written for gentoo, and it might not match your setup, but maybe you can either get some ideas from it or adapt it to your situation.

[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

Sorry I can't be of more help, but I hope that points you in the right direction.

---

### Post by isharra on 2007-09-23
> **JustinMorris said:**
> I thought I could try to revive this thread, as I am still trying to figure this one out.  I have read a lot and tried many things.  If you take a look at my attachment in the first post you should get a good idea of what I wish to accomplish with the "open" wireless router going thru the ubuntu box.  Please help!

First a really basic question, how are the ROUTERS being configured?

Routers from the same manufacturer  tend to be configured to all have the same ip address and share the same ports, so your setup usually won't work out of the box. The shared router needs to have the ubuntu server configured as it's gateway and it must have a distinct local ip address than the local router. The local router needs to have a route set to reach the shared machines and it needs to be set to masquerade/nat those connections. Ubuntu server needs to set up to forward connections from one to the other.

Simplified example (there are many ways to do this):

local router:
ip address 192.168.1.1
gateway via comcast adapter
add route to 192.168.2.0/24 via 192.168.1.50 (ubuntu server)
add rule to masquerade/nat 192.168.2.0/24 (do it at this router to best preserve multiport network connections.)

ubuntu server:
local address 192.168.1.50 (eth0)
shared address 192.168.2.1 (eth1)
set up iptables rules just like any example with eth0 being the "external" adapter and eth1 being the "internal" adapter. The distinct address ranges are in order for you to be able to easily adapt the many examples on the net for what limiting you might want to do. 

shared router:
ip address 192.168.2.2
gateway via 192.168.2.1 (ubuntu server)
disable masquerade/nat if you want to control/limit connections via your ubuntu server (if left enabled all your neighbors would appear to only have the one ip address)
change the dhcp server inside to serve addresses in the 192.168.2.x range if you are wanting to dhcp from here (personally, i'd be paranoid and set up fixed addresses tied to mac addresses in addition to wpa2 but that's dependent on your router.)

[edited for clarity]

---

