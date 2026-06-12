---
title: "problem with linksys befsr41 and 2wire"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by pacofvf on 2008-04-30
i have this problem i have a 2wire modem-router that is connected to internet and i have like a "subnet" with a linksys befsr41 router, what do i have to do??

---

### Post by AjitDingankar on 2009-04-04
Any ideas? I have a similar config, with two Ubuntu machines connected to a 
BEFSR81 router that is conencted to 2wire DSL gateway.

---

### Post by sledjockey on 2009-04-06
> **pacofvf said:**
> i have this problem i have a 2wire modem-router that is connected to internet and i have like a "subnet" with a linksys befsr41 router, what do i have to do??

So you are saying that it is NAT'ed with some private IP network that is being distributed by some DHCP server?

There isn't much information here to work with as to what problem you are having..

Does your NetworkManager say that you are connected?  If so, what do the connection settings say?

---

### Post by AjitDingankar on 2009-04-14
Thanks, sledjockey! Since the original poster hasn't answered yet, I'll describe 
my situation. I have the following configuration: 

Phone line ---> 2wire wireless modem router (192.168.1.254) 
                  ---> linksys BEFSR81 (192.168.1.1) 
                         ---> host1
                         ---> host2 

Network settings: 
Domain (and "Search domains") gateway.2wire.net 
DNS Server: 192.168.1.254 

I could connect to the internet, but couldn't ssh from host1 to host2 or 
vice versa. 

The problem seems to be resolved now (at least temporarily) after I added 
192.168.1.1 as a DNS server; but I remember I had tried this before and it 
didn't work, neither did it "stick".

---

