---
title: "UFW allowing specfic range of IP's"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by CaptainMark on 2014-04-18
I know I can allow access to a specific port to all ip's on my lan with UFW by using ```
sudo ufw allow from 192.168.1.0/24 to any port 9091
```(Using transmission UI port just as an example)

But I would like if possible to be more specific, my router is configured to dish out IP's automatically between the range of 192.168.1.002 to 192.168.1.100  for temporary devices and visitors, however the range from 192.168.1.101 and beyond is reserved for specfic mac addresses (just my own devices really desktop/laptop/servers/tablet/phone)

So my question would be is it possible to amend this ufw command to allow access to this specific port from device IPs ending between say 101-199 and to exclude IPs ending in 002-100?
The main reason being to make sure friends visiting (or heaven forbid, a digital intruder) don't either try to or accidentally mess with any of my services running on the servers, (they are all protected in some form or another anyway but there's no such thing as too much security right?)

My understanding of routers/networking is pretty noobish so I totally won't be able to understand if answers involve customising subnets or some such shenanigans, in other words please keep it relatively beginner friendly.

Thanks for any assistance
Regards
Mark

---

### Post by TheFu on 2014-04-18
Yes, it is possible.  All those client machines need is DHCP, DNS, HTTP/HTTPS and perhaps SMTP/IMAP/POP3 (both secure and non-secure ports).  If the Ubuntu machine isn't used for any of those things, they can just block everything from those other IP ranges.

You didn't ask "how", so I'll just say that the ufw manpage is pretty clear on that.  

man ufw
or 
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Now - that I'd do is setup DHCP static reservations for my devices on lower IP addresses 1-127, then let non-reserved DHCP be above x.x.x.192-223.   Then you can use an easier subnet mask to block just those.  Use a network calculator to get that subnet mask. Because of the way that subnetting works, this would be much easier than what you are asking.

Please realize that nothing would stop someone from setting a static IP outside that range on their computers, which would bypass your firewall.  It would be better to deny everything, then only allow the specific ports from other specific IPs in.  Rather than deal with all of that, a 2nd $15 "guest" wifi router is easier - put all the guests on a different subnet.

---

