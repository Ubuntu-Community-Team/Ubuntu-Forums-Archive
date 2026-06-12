---
title: "IPv6 routing?"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by Garyu on 2006-09-12
I want to try setting up my home network with IPv6. Problem is, I can't find any routers for sale with IPv6 support. So I figured that I could setup my old Celeron-900MHz as a router with IPv6, but then I need to translate that into IPv4 to get out on the internet. All the howto's and other threads I can find only deal with DISABLING IPv6, and that is obviously not what I want.

My current setup is that my 10Mbit internet cable goes into a D-Link DI-604 router which is hooking up my own computer (with ubuntu), my Celeron-900 (with xubuntu) and my roomie's laptop (running winxp pro). 

What I want is for the internet connection to go straight into my Celeron-900 on one ethernet card (IPv4), and then use the other ethernet card to output IPv6 to my ubuntu computer. I know, not much point, but I just want to do this as an experiment to see how IPv6 works.

But I don't even know anything about setting up IPv4-routers, even less using IPv4 on eth0 and IPv6 on eth1. So any pointers would be helpful. Maybe someone knows of a good howto out there on the net for linux servers? There has to be other people trying this, but I can't seem to find much help...

---

### Post by tbonius on 2006-09-12
Here is a can of worms.  You can do native IPv6 from the Internet to your Ubuntu router.. and propogated to your internal network.  This is acheived using a tunnel broker or top level IPv6 aggregator.  You can also setup your Ubuntu server as an aggregator to make your internal network IPv6.  You then can either do IPv6 tunneling or translation.  THe question is.. of these scenarios.. which do you want to do?

Read the documentation at 

[http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/](http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/)

[http://www.kame.net/](http://www.kame.net/)

[http://ipv6.he.net/](http://ipv6.he.net/)

and shameless plug:

[http://www.section6.net/wiki/index.php/Main_Page](http://www.section6.net/wiki/index.php/Main_Page)

Some of the docs deal more with BSD variants.. but the concepts are the same.  Let me know if you need any additional help as I always love to help people get into IPv6

T

---

### Post by Garyu on 2006-09-13
wait, you kind of lost me here. are you saying that I can configure for 100% IPv6 without using IPv4 towards my internet provider? Because when I first installed ubuntu I managed to set it to IPv6 only and my router wouldn't rout me (if you understand what I mean - my net was down). 

I have to go to work now, so I only had time to browse through those links, but they seem rather high level. For example, the section6 page on IPv6 starts by saying "Set the following options in your kernel" and then goes on with a bit of code. It also says to add an stf device manually. But I don't know where or how to set options for my kernel, and I don't know how to add devices.

If this is all the help available, maybe I should just realize that I need to learn more before diving into these kinds of projects... :P

---

### Post by tbonius on 2006-09-13
No.. you still need IPv4 to connect to your ISP.  Unfortunately most ISPs in the U.S. have not converted over.. but you can still use a tunnel broker to assign a public IPv6 address range (that can propogate to your internal LAN as well so that they are IPV4 NAT'ed as well as IPV6) through your V4 address and access publicly available IPv6 services.  Or.. you can make your internal network IPv6 only and use a translation virtual adapter through your firewall.. acting as an Ipv4/V6 proxy.

---

### Post by Garyu on 2006-09-13
> **tbonius said:**
>  Or.. you can make your internal network IPv6 only and use a translation virtual adapter through your firewall.. acting as an Ipv4/V6 proxy.

yes, this is what I want. IPv6 only in my home LAN and then use my xubuntu machine as a server with routing and so on. 

But the things they say at the section6 link you gave me... Where do I set options in my kernel? Are they saying that I need to recompile my kernel?

---

### Post by tbonius on 2006-09-13
The documentation on Section6 refers to BSD with its IPv6 transitive interface.  The concepts are there for understanding how IPv6 works.  In the case of this document you would be using whatever aggregator exists out on a public network.. or you can use a specific tunnel broker like Hurricane Electric.

In this case, your Linux kernel should already be configured for IPv6 addressing (You just need to configure a transitive interface), and simply needs an aggregator service installed on your system.  This "Route Advertisement Daemon" is a package called "radvd" in Ubuntu.  Install this and check out the documentation for it.

The transitive interface for Linux is known as the SIT device (Simple Internet Transition interface).  Once configured you can setup the Aggregator to hand out a network address range (much like DHCP.. only not) and then setup firewall rules to pass IPv6 traffic.  Be sure and allow "net.ipv6.ip_forward = 1" for passing out V6 traffic to whatever interface you wish.  

Read the links carefully I posted earlier.. theres lots of good info there.. and make sure other services (like BIND) are configured to handle IPv6 (AAAA records) as well.

T

---

