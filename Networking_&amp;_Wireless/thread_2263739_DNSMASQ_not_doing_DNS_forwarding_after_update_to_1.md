---
title: "DNSMASQ not doing DNS forwarding after update to 14.10"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by libransser on 2015-02-02
After updating my Ubuntu Desktop to 14.10, Dnsmasq doesn't seem to forward the DNS requests of other machines from the same local network.

For local web development I set up Dnsmasq on my Ubuntu Desktop laptop for the handling of *.dev (development) domains, with Apache2 as the web server.

This allowed me to access and test sites in my iPad, by changing the wireless network DNS setting to point to my laptop instead of the router (that otherwise is the "normal" DNS server), while allowing me to surf the web normally.

This set up worked fine before the update to 14.10. I didn't test it immediatly after the update, but now that I want to use it, it doesn't seem to work anymore.

Both, the iPad and the laptop are visible to each other inside the local network. Both have fixed IP addresses. I can reach the iPad via ping, and the laptop's Apache2 server works fine when I enter the IP address in Safari in the iPad.

But when I change the iPad's DNS server to point to my laptop, not only the .dev local domain doesn't work, I'm also unable to access any other website (Safari tells me "could not open the page because the server stopped responding"). I can access public websites if I enter their IP address directly. On my laptop everything works fine.

That has been the most telling sign that Dnsmasq isn't forwarding the DNS requests, but so far I haven't been able to find a solution.

I have been googling around and have been toying with the Dnsmasq configuration but so far no luck.

After reading for a while I tried several combinations with the Dnsmasq configuration options ***address***, ***listen-address*** and ***server*** in ***/etc/dnsmasq.conf*** but to no avail.

One of those also included uncommenting the ***prepend domain-name-servers 127.0.0.1*** line in ***/etc/dhcp3/dhclient.conf*** but that hasn't worked either.

I have looked into ***/var/log/syslog*** but I'm not able to decypher what it is telling me, or if it is useful at all.

I even reinstalled Dnsmasq to see if that fixed something, but no.

Does anyone has any idea what else can I try or where else to look?

---

