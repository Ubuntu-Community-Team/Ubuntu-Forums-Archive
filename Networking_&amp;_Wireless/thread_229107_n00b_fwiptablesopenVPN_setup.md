---
title: "n00b fw/iptables/openVPN setup?"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by tivoklr on 2006-08-04
Hi,

Newish to linux, long time osx user.

I want to make sure I'm on the right track here.

I have a Ubuntu box version 6.06.1 and I would like to have it replace a Linksys BEFVP41 that is acting as a firewall, nat/port forwarding device and VPN server.

Now the reason I'm ditching the Linksys isn't that it isn't working for me, but that my network has changed.

I now have 2 public IP addresses instead of one. I needed to have ports 80 and 443 available to two different internal computers and this seemed to be the way to go. This is a xDSL line with a Cisco 678 dsl modem. The eth0 address of the router is the gateway address for my block of IP's from Qwest.

IP 1 needs to point to my internal network of 10.0.0.0 with several ports being forwarded to various machines, 25, 80, 443, 5800-5900, and some other oddballs for specific sw. Not all ports point to the same ip, 80 and 443 point to the webserver, 25 points to the Barracuda spam firewall, etc.

IP 2 needs to point just ports 80 and 443 to one box on the same 10.0.0.0 network.

I also need to add some static routes for my 6 offsite networks that all come in via T1, blah blah. That shouldn't be too bad.

I then need to setup OpenVPN on the 1st IP so that 2 offsite workers can VPN in, one running XP and one running OSX.

And that's it. No DHCP, no DNS, no mail, web, etc...

Sound doable, reasonable with ubuntu?

Should I have 2 nics, one for the publically reachable IP's and one to connect to the internal network?

Any suggestions, hints, etc? I'm not looking for a walkthrough here, but some light reading on iptables and such would be good.

Thanks for looking!

tivoklr

---

### Post by tivoklr on 2006-08-06
Nobody has ANY thoughts on this? I need to decide whether this is workable or not.

Thanks!

---

### Post by hanasaki on 2006-12-09
Ever get this to work?  How?

---

