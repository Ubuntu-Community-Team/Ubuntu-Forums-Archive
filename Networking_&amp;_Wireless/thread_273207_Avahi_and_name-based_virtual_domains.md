---
title: "Avahi and name-based virtual domains"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by crischan on 2006-10-07
Hi,
I have set up a apache2 with a main site and two additional name-based virtual hosts. The names of the virtual hosts are set in /etc/hosts, so there are only available from my machine. Using mod-dnssd, our MacBooks discover the two name based virtual hosts under their name and the main host as acme.local (acme being the hostname of the linux-powered laptop). But as they don't know about the IPs of the two host names (ttb.acme and g2.acme) they can not access these two.
Thus my question: How can I broadcast another name for my network address such as g2.acme.local or at least g2.local? Or is there even a way to broadcast the names "acme", "g2.acme" and "ttb.acme" for the same (my) IP address without the .local domain? (Thus basically, how can I broadcast another address for my IP using avahi to enable name-based virtual hosts with avahi?

Any thoughts are welcome!

---

