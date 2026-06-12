---
title: "I really want to download torrents, but.."
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by El Lance-O on 2007-05-06
I can't get port forwarding to work.

I'm currently using my neighbor's wifi, but I can access his router settings no problem,

I forwarded the correct ports, but still the no incoming connections work.

Can anyone help?

---

### Post by gejr on 2007-05-06
Sounds like there's a firewall somewhere blocking.

See if you've got iptables running or something. iptables -L. Shouldn't be any rules there on a fresh ubuntu install.

Could also be a firewall on the router that's blocking incoming connections on the port you're trying to forward.

---

### Post by El Lance-O on 2007-05-06
Well I have access to the router setup to forward ports, and no firewall is active...

Here's what I got with iptables -L

> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       

---

### Post by El Lance-O on 2007-05-06
bump

Please help?

Being able to download torrents would help me immensely right now.

---

### Post by mills on 2007-05-06
try downloading firestarter (a gui for iptables)

and configure the ports in the policy tab (inbound policy)

---

### Post by El Lance-O on 2007-05-06
I don't have any kind of firewall running though, and neither does the router, I turned that off.

---

### Post by El Lance-O on 2007-05-07
bump

---

### Post by bigkahoona on 2007-05-07
What sort of client are you using? In Azureus, for example, there is a little dot in the bottom that's either green or red, depending whether the NAT is working correctly or not.
My guess is that somehow the port is still not forwarded correctly.
And switching off the whole firewall is *definitely* not a solution and very reckless. Your friend's router should either have a table that you can enter the WAN source and LAN destination IP and ports into for whatever you want to be NATted or there should be some form of service definitions that you can create and edit (mine does that) and which you will then have to enable. For example, I have a service definition called "azureus" which starts and ends at port 33322 for TCP and UDP. I have then activated that service for my static LAN IP and changed the azureus settings to use that port.
But it would sure help to know the exact model of the router used.

---

### Post by mainely_linux on 2007-05-07
You need to make sure your IP is what you have forwarded the ports to in the router settings.  Out of the box, most routers use DHCP.  You'll probably have the best luck if you set a static IP that communicates on the routers network and forward the ports (tcp/udp) accordingly.

HTH

---

### Post by fakie_flip on 2007-05-07
What torrent client are you using? I know with Bittornado, it doesn't use the standard torrent ports by default, but you can configure it to.

---

### Post by El Lance-O on 2007-05-07
Well I've tried to use uTorrent, Azureus, BitTorrent, and BitTornado...none of them work, and Nicotine is disgustingly slow (2 kbps).

The router is a Linksys WRT54G, and the port forward screen looks like this:

> [IMG]http://img367.imageshack.us/img367/7791/screenshotforwardswiftfia6.png[/IMG]

Doesn't matter what ports I forward, nothing works.

---

### Post by fakie_flip on 2007-05-07
The ports you are supposed to be forwarding are 6881-6999 tcp. Also you are forwarding them to the wrong ip address, no wonder. You have them forwarded to your router's ip address 192.168.1.1 which makes no sense. Find out what your ip is by doing this.

ifconfig | grep 192

It is probably 192.168.1.100 or 101 on the end since you are using a router similar to mine.

---

### Post by El Lance-O on 2007-05-07
Fantastic! You were right, it was 192.168.1.101

Thank you all for your help!

---

### Post by fakie_flip on 2007-05-08
You're welcome.

---

### Post by kelvin spratt on 2007-05-08
go to [http://portforward.com/](http://portforward.com/) will explain it all graphically how to get port forwarding to work correctly for most routers and p to p aplications

---

