---
title: "Ubuntu as gateway, not all pages accessible."
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by albuemil on 2007-01-09
Hy.

I've got a server with Ubuntu 6.10 on it, and 2 XP machines that connect to the net trough it.

The server connects using PPPoe.
My problem is that I can't access a few sites from the XP machines, but i can from the linux server.

One example is the [http://my.opera.com](http://my.opera.com).


On the Ubuntu server :
If i ping it i get 213.236.208.98 as the IP, i can load it up in Lynx and it shows up correctly, using either the name or the IP.

On the XP machine :
If i ping it i get 213.326.208.98 as the IP, but i can't load it up in Internet Explorer and Opera. I've tried both with the name and IP, but it just doesn't load up.

I've tried setting the XP machine to use the DHCP from the Ubuntu server, and also with statip IP, but it just doesn't want to work. I've tought its a DNS problem, but i just can't understand why the linux can see the site whyle the XP machines not :confused: 

Does anybody have any ideea what could be the problem ?

P.S. i've tried searching the forum, but didn't find anything similar, and i've also disabled IPv6 but that didn't help either.

I'm really getting desperate, any help would be appreciated. I've even tought about installing a proxy server on the ubuntu if that would help.

---

### Post by albuemil on 2007-01-10
The funny part is that i was able to go to [www.opera.com](www.opera.com) but not to my.opera.com which seems very strange.:confused: 

I didn't find out what was the problem, but i've managed to get a workaround, I've installed the Squid proxy server, and now I can browse the net without problems.

I'm happy it's working with squid, i'll sticj with it for now:D

---

