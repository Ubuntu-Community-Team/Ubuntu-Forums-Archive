---
title: "Networking - DNS - Search Domains"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by mastercomputerwizard on 2008-01-31
Just want to make sure I have this right.
I have a local domain with local DNS servers (172.16.X.X) that forward to the outside world. I have set up the static IP information in Gutsy and the DNS servers using the local IP's of my two DNS servers.
I put in my local domain name domainname.local in the search domains field under the DNS  tab. (I assume this correct?)  I know normally it is your ISP name (domainname.com).
Everything seems to be working fine.
For piece of mind what to make sure this correct before I do a bunch of systems on our network.

Thanks!

---

### Post by netztier on 2008-01-31
> **mastercomputerwizard said:**
> 
I put in my local domain name domainname.local in the search domains field under the DNS  tab. (I assume this correct?) 

Using **.local** als your local TopLevelDomain is **not recommended** as this conflicts with zeroconf/avahi's use of this domain for multicast-based name resolution. If avahi detects that <something>.local is in use, it may disactivate itself with unwanted side effects - such as DAAPd (iTunes) music sharing no longer working.

I suggest you use another domain name that does not in any way conflict with a TLD being used on the Internet.

regards

Marc

---

### Post by mastercomputerwizard on 2008-01-31
Thanks for the quick reply.....

---

