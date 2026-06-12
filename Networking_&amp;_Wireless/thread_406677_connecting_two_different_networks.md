---
title: "connecting two different networks"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by nardus on 2007-04-11
Hi there...

Probably something like this was asked/answered somewhere else in the forum, but I wasn't able to find it, so here I go.

I have the following situation:
Where I work we are about to surpass 255 computers/devices in the network, and we are about to be "out" of IPs in the very simple network that's in place.

I'd like to open a new network so new computer/devices are set up in a new range of addresses.

Set up is like this:
Ubuntu 6.04 Server, serving as transparent proxy + firewall + intranet server for the organization, with two network adapters.
* eth0  (10.10.10.1, connected directly to internet)
* eth1 (172.16.1.200, connected to the local network, with an alias as 172.16.1.250)

The network is 172.16.1.x

I would like to set up new machines in the 172.16.0.x range, adding a new ip to the server as 172.16.0.250 for these machines to use as a gateway, and for these machines to be able to connect transparently to other machines/servers in the 172.16.1.x range. (New machines would be in the same physical network as the old)

I am thinking that adding a couple of iptables rules would solve my situation, but I am not very sure if that's would be the case at all, or how should I construct these rules if they really are the answer.

Hopefully the question is not hopelessly stupid, and someone can lend a hand.

Thanks in advance for any clues or advice.

Regards,

I.-

---

### Post by nardus on 2007-04-12
Anyone know anything about it?
Help would be very appreciated!

Thanks again.

Regards,

I.-

---

### Post by leshaussebons on 2007-04-12
if my long computing courses are not so far away from my mind, you could seek in the ip mask configuration :

255.255.255.0 works for only the same ip table ...
changing the 3rd 255 to a lower value allows you to use the IP 172.160.1, 2 ,3 etc values, in the same network

in french : an explanation of SUB networks and masks : [http://www.commentcamarche.net/internet/ip.php3](http://www.commentcamarche.net/internet/ip.php3)

I wasnt able to find a explanation in english now, try google but I guess you request will be fullfiled

---

### Post by leshaussebons on 2007-04-12
here it is !!

[http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork)

sorry for the double post :)

---

### Post by computerease on 2007-04-12
I concur with the previous responder.  Some months back (like six) I worked out a three tiered network arrangement for a network, with the bottom level having only access to its own set (192.168.10.x), the second level able to access its own range and the first range (192.168.11.x) and the third level being able to access all three (192.168.12.x).   I don't have that material readily available to forward, but a google search with the terms "subnet mask" +"ip range" should produce a plethora of links, some of which will specifically discuss the subnetting techniques.  A search for "subnet calculator" +download should also give you the calculator to make this a bit more simple.

---

### Post by nardus on 2007-04-12
Preferrably, I'd like to leave the configuration of the existing machines/devices as it stands (netmask 255.255.255.0).

If I understand correctly, the Ubuntu box should be able to route between the two networks (172.16.1.0/24 and 172.16.0.0/24), wouldn't it?

Thanks for your help.

Regards,

I.-

---

