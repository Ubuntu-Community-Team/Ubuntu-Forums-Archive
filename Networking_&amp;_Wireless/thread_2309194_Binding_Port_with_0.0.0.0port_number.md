---
title: "Binding Port with 0.0.0.0:port_number"
date: 2016-01-08
forum: Networking &amp; Wireless
---

### Post by beginner3 on 2016-01-08
i'm new to ubuntu and networking too 
i've problem with binding port like 7700 
when i connected it i got 0.0.0.0/0.0.0.0:7700
i need to listen to my ip address like 192.168.x.x:7700 

i disabled ipv6 .. but no change 
i searched how can i change it but couldn't find a solution 
Hope you can help me

i'm usinf WI-Fi connection , if you need any details, i can provide you

---

### Post by ian-weisser on 2016-01-08
See [https://en.wikipedia.org/wiki/0.0.0.0](https://en.wikipedia.org/wiki/0.0.0.0)
A process binding to 0.0.0.0 should listen on all IP addresses assigned to that host, including 192.168.x.x.

---

### Post by beginner3 on 2016-01-08
> **ian-weisser said:**
> See [https://en.wikipedia.org/wiki/0.0.0.0](https://en.wikipedia.org/wiki/0.0.0.0)
A process binding to 0.0.0.0 should listen on all IP addresses assigned to that host, including 192.168.x.x.

I've error in binding that port and any port i use like 6703 6700 6710 7700 
error said 
failed to bind 0.0.0.0:0.0.0.0/7700  address already in use 

But i checked address and couldn't find anything wrong except my process

---

