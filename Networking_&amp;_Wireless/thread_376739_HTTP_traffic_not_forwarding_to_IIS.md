---
title: "HTTP traffic not forwarding to IIS"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by colinhumber on 2007-03-05
Hi,

Sorry if this has been answered somewhere else.

I just installed Ubuntu server on a box and have it placed as a firewall/router for the rest of my network. Inside the LAN I have a Windows 2003 server with IIS installed as well as some other computers.

Before I installed the Linux server I had a Linksys WRT54G router that would share the internet connection and forward my HTTP port 80 traffic to my IIS server. This, however, is not working with port 80 traffic forwarded using Firestarter on the Linux server. Any traffic on port 80 goes to the Apache server installed instead of being forwarded.

Here's the current setup:

_Linux box_
eth0: DHCP to cable modem
eth1: 192.168.1.1 (gateway to LAN)

Apache2 server installed
Firewall forwarding HTTP (port 80) traffic to 192.168.1.20

_Windows Server 2003 box_
NIC 1: 192.168.1.20

IIS 6.0 installed


My internet is being shared correctly so the majority of the firewall/NAT functions are working properly, all except the HTTP forwarding. When Apache2 is turned on hitting my WAN address goes directly to the Apache2 site. When it's off I just get a site not found error. Eventually I'm going to have Apache2 and IIS installed on different ports, I just figured for now I'd just keep IIS at port 80 since I don't use Apache at the moment.

Thanks in advance, hope that all makes sense.

---

### Post by Johnathon on 2007-03-05
It sounds like your firewall forwarding is failing.

How used are you to command line configs? If very, then I'd reccomend firehol as a easy-to gonfigure (after reading up on it) firewall, that would make doing stuff like that stupidly easy (one line in configs).
[http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)

HTH

---

### Post by colinhumber on 2007-03-05
Thanks for the response. I'll take a look at FireHOL. Odd, though...when I hit my domain from outside the LAN it works fine. It seems like it's just when I hit the WAN address from within the LAN that the forwarding doesn't work properly.

I have my BitTorrent ports being forwarded properly, so I don't know that it's the firewall. At any rate, I'll have a look at that link you sent.

---

