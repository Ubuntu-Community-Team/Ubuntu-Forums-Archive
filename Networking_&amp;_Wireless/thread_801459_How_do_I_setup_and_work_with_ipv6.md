---
title: "How do I setup and work with ipv6"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by rgeddes on 2008-05-20
I'm interested in getting my internal network running on ipv6 to learn about using it.

I have a computer on a network with bind9 set up as a caching DNS server.  It works fine for that particular computer.  I want other computers on my network to be able to use the caching DNS server as well.  Netstat tells me that the caching DNS server (named) is listening on a tcp6 ports 53 and 953.  My other computers can't access the caching nameserver... I think it's because of the ipv6 configuration of eth0... the computers show different network prefixes for their ipv6 addresses.

I realize I could make the caching nameserver on an ipv4 port, but I would like to venture into using ipv6.

Is there a recommended way to set up and work with ipv6... at this point I'd be looking at using it only for my internal network.  

Thanks
Richard

---

