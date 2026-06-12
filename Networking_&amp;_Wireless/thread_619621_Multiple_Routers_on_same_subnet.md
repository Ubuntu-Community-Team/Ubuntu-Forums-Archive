---
title: "Multiple Routers on same subnet"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by bloodniece on 2007-11-21
What are the pitfalls of having multiple wireless and wired  routers on the same subnet?
All our receiving IP  addresses from my domain's DHCP server.  Some are setup with ethernet going in the the Internet port allowing the router to act as a local DHCP server for wireless clientss.  Some of my routers are setup with nothing connected to the Internet port and one of the 4 ports on the router is connected to a 20  port switch.  This way clients get their IP from the domain's DHCP server instead of the local router's DHCP.   Is this a bad idea?  Should I be using this is RIP mode instead of gateway mode?

---

### Post by mellowd on 2007-11-23
It sounds far too complex having multiple routers plugged into a switch. How exactly is the network set up right now? (drawing if possible) How many clients of each type connect and how many switches/routers are there in total?

---

### Post by bloodniece on 2007-11-24
They are not all plugged into the same switch.  But they are all on the same subnet.

2 bonded T1 are coming in for Internet into a Juniper firewall.  From there to a Dell powerconnect. From the powerconnect to 4 fiber media convertors.  Each fiber run terminates in a separate building  with a dell powerconnect and a fiber media converter.  Each of the aforementioned buildings has a wireless router on the switch.   3 buildings are connected to one that has fiber by Cisco Aitonet WL bridges using 802.11G and least congested channel.  Also, one building is connected using Cisco LongReachEthernet.  tada!  my network.

Each powerconnect has around 10 to 15 nodes attached.

---

### Post by mellowd on 2007-11-25
With this particular setup its gets a bit difficult to troubleshoot when a problem crops up. I would have possibly seperated each building into its own subnet, a /30 subnet would do. 

Where in this setup is the domain controller? In one of the 4 end buildings or closer to the netscreen? what model of netscrren have you got? (So I can have a look at the mount of ports it has)

---

### Post by bloodniece on 2007-11-30
I was trying to keep it simple with one subnet.  Netscreen is NS5GT.
DC is in same building on same switch as the NS5GT.

---

### Post by psusi on 2007-11-30
Either just use wireless access points, or disable the routing/nat functionality on the wireless routers and use them just for access points.  There should only be one dhcp server active on the network.

---

### Post by bloodniece on 2007-11-30
I noticed with the  Linksys wireless routers, that if you plug the network/wan side of things in with the lan, DHCP is diabled for the router and passed on to the master DHCP server.   Is this bad form?

I wish I could replace all with access points, but we're cheap and a non-profit and working with what we have.

---

### Post by bloodniece on 2007-12-04
Ok, the solution was to install DD-WRT fimware on the routers and disable DHCP and set the Internet connection type to none/disabled.  Also, I assigned the WAN port to switch and fowarded DHCP to our master DHCP server.  I gave the routers static IPs on our subnet and used the same gateway and DNS for all.  Presto! It works like a charm.

Thanks to all for your suggestions.

See:
[http://www.dd-wrt.com/wiki/index.php/Wireless_Access_Point](http://www.dd-wrt.com/wiki/index.php/Wireless_Access_Point)

---

