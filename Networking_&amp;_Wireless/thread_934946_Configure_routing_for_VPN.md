---
title: "Configure routing for VPN"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by gertvanthienen on 2008-10-01
L.S.,

With the Hardy release, when creating a PPTP VPN connection from NetworkManager, there was an option to specify IP address ranges to use the VPN.  E.g. you could specify that all traffic for 10.1.10.0/24 had to go through the VPN and everything else could just use the default gateway.

I'm now experimenting with Ibex and this option is no longer available in the VPN.  There is however an option to define routing on the VPN connection, so I guess you can do the same thing there now.  How does the 10.1.10.0/24 translate into routing table entries?  How do I know the IP address for the gateway to be used on the entry?

Thanks for your help,

Gert

---

### Post by jtoppine on 2008-10-14
Hi. I just registered to ask this same question. It seems that, when connected, all traffic is routed through VPN (vpnc). Which means for me that:

- internet access is slower
- all traffic goes through my workplace, which is kind of a privacy issue, maybe
- some applications like pidgin stop working when using vpn

In Hardy Network Manager there was this option to only use VPN for certain addresses, but 

There were other problems with the Hardy version, so I can not revert back to that.

In the new version there is this Routes -dialog, but I do not understand it =)

It looks like this;

Editing IPv4 routes for [connection]

You can add entries to a table with following columns: Address, Prefix, Gateway and Metric

There is also a checkbox "Ignore automatically obtained routes"

How could I make it so that traffic to only certain IP addresses go through VPN?

Thanks for your time and help.

---

### Post by ngc2997 on 2008-10-31
Hi,

this is something that I am interested in, too. Having upgraded to Intrepid just yesterday, my old VPN connection settings were gone, so I had to enter a new connection and am now stuck with configuring the routing options as mentioned above.

[Apart from that, network-manager-pptp seems to have severe problems with saving configuration options properly. Also, there is no possibility to define a specific value for MRU, thus my VPN connection keeps dropping frequently due to a read error, but that is another story..]

Best wishes,
Karsten

---

### Post by mavl4219 on 2008-11-01
Jp, the same problem in my case. I used to have just few of the network addressed routed through the VPN (ppp0) (the ones we use at work), but other traffic went through my eth0 interface...

There is a new user interface in ibex, and i'm not sure how to use it...

---

### Post by JazzyPenguin on 2008-11-01
Yes, I too am looking to configure specific IP addresses to be access by the VPN only with all other traffic using the default gateway.   Some help on deciphering the routing table would be great.

---

### Post by mavl4219 on 2008-11-02
I think i got it working!

In the old user interface, i used to write 192.168.10.0/24, to communicate with the 192.168.10.x network. In the new one, i've added a new route with the following configuration:

Address: 192.168.10.0
Prefix: 24
Gateway: 0.0.0.0
Metric: 0

It seems to be working...

---

### Post by atlanta800 on 2008-11-02
> **mavl4219 said:**
> I think i got it working!

In the old user interface, i used to write 192.168.10.0/24, to communicate with the 192.168.10.x network. In the new one, i've added a new route with the following configuration:

Address: 192.168.10.0
Prefix: 24
Gateway: 0.0.0.0
Metric: 0

It seems to be working...

Yup that worked for me as well.

---

### Post by CuraHack on 2008-11-08
Hi it didn't work for me, I want to know what do these names mean [in detailed explination]
[LIST]
[*]Prefix
[*]Gateway
[*]Metric
[/LIST]

Thank you...

---

### Post by AntiHeroJoe on 2008-11-12
If I set up my routing as described, I can access the internet without using the VPN, BUT when trying to use Terminal Server Client, it refuses to connect to the IP I had specified in the routing. If I remove the routing, the Terminal Server Client will connect just fine. I don't know what any of the things in the routing means, so I can't really figure out what would need changing. Any ideas?

EDIT: When I AM able to access the internet, it's so much slooooower than it used to be! Anyone know why this is?

---

### Post by paulroy on 2009-10-24
Hello,

i Have got a working solution for Ubuntu 9.04
my setup
pptp vpn client connecting to company on 10.0.7.x
main company network is on 10.0.0.x
(for firewall reasons the pptp network and server network are in different ip zone's)

i order to make connection:
open the edit vpn connections window
under the IPv4 settings tab choose routes
add route 
address 10.0.0.0 (= the network address)
netmask 255.0.0.0 (the class 1 netmask) 
gateway 10.0.7.254 (the address of your router on the pptp network)

set 'use this connection only for resources on this network' 

voila, that's it
good luck

(maybe a next user can confirm these settings)

cheers

i've gotten the inspiration from
[http://www.craigmayhew.com/blog/2009/07/fixing-ubuntu-9-04-vp]("http://www.craigmayhew.com/blog/2009/07/fixing-ubuntu-9-04-vpn-adding-remote-network-to-routing-table/")
but it's not entirely correct there

---

### Post by Funkmob on 2010-12-15
Hooray, paulroy. That's exactly the information I've been searching for. Thank you very much! (more than one year later)

---

