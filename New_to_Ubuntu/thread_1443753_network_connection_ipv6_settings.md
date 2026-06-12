---
title: "network connection ipv6 settings"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by deathintheafternoon on 2010-03-31
Where can I find an explanation of the "network connection-->ipv6 settings" fields?  

I am using Karmic Koala 9.10 

I have a "41" tunnel set up via a tunnel broker (HE).  I can type IPv6 addresses in my firefox browser if I use the address [http://[xxxx::xxxx]]("http://%5Bxxxx::xxxx%5D"), but I can't get domain names for IPV6 sites to resolve.  Example, I can type the IPv6 for Kame.net or ipv6.google.com and get the page, but not if i type the domain name.

I have a DNS server available from the tunnel broker (plus google public).  I can ping6 the DNS AAAA server, and my router is configured with the default DNS/DNS 6 servers.

I went to network connection in Ubuntu and clicked the IPV6 Settings tab.  I tried selecting automatic, then apply, but this does not seem to work.  I don't understand the fields being asked for under the "automatic-address only" and "manual" options.  I know the IPV6 of my DNS server, but I'm supposed to enter in "Search Domains".  Also I don't understand if I'm supposed to set "Routes" or not, and if so, what to put?  

I have all of my IP addresses for my hosts, gateway, and DNS servers, I'm just not sure I understand what I'm supposed to enter in each box.

Also, if this might be a browser setting issue with firefox, not a problem with my network settings in Ubuntu, please let me know.  I tried googling for info about that but didn't find much.

Thanks.

---

### Post by wojox on 2010-03-31
Here's what I used to configure mine: [Running IPv6 in practice]("http://www.debian-administration.org/article/Running_IPv6_in_practice")

---

### Post by deathintheafternoon on 2010-03-31
> **wojox said:**
> Here's what I used to configure mine: [Running IPv6 in practice]("http://www.debian-administration.org/article/Running_IPv6_in_practice")
Thanks.  I think I will just try setting up a local cache with BIND, like that example.  Thanks again.

---

### Post by wojox on 2010-03-31
Welcome. ;)

---

