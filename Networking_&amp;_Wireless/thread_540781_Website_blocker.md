---
title: "Website blocker??"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by klanman8908 on 2007-09-02
I am searching for an effective way to block web proxies on port 80 and 443.  Currently we have a sonic wall that takes care of the port 80 problem but people just add and s to the http making it https and then they can get to proxies and go anywhere.  

Currently our setup is also using a linux router (server install) using iptables.  The box is set up as a transparent bridge and filters all traffic on port 80 and 443.  The biggest problem is when iptables is given a url as a destination it does the DNS lookup and blocks all the ips making the site impossible to get too.  However it is blocking web servers rather than websites.

We have looked in to dansguardian and squid but that only filters 80 and we need port 443 filtering.  We can't just block the port because come legit sites use it.  I'm a point where I can't think of anything else to try.  Any help would be greatly appreciated.

Thanks in Advance



Kyle

---

