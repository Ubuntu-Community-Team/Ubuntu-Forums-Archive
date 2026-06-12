---
title: "DNS redirection..."
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by kwiki on 2007-03-23
hi linux gurus

I've install bind9 on my Ubuntu Box (edgy elf).. as far as i know i configure it well. i can ping all the domain name that i created. my problem is how will i redirect this one: 
My DNS server's ip is 121.x.x.x (ubuntu)
and my APACHE server's ip 10.x.x.x (Red Hat)

when i entering [www.mydns.com](www.mydns.com) the webpage displays itself but when i key in to the browser 121.x.x.x the webpage doesn't show up.. what can be the problem? and how can i redirect 121.x.x.x to [www.mydns.com?](www.mydns.com?)

thanks....

---

### Post by Braken on 2007-03-23
Are you sure it is a DNS resolution problem? When setting up Apache it is possible for it to ignore IP Address based URLs and only to respond to FQDN URLs.

EG. 192.168.0.1 would display a blank page
but [www.intranet.local](www.intranet.local) would display the local intranet

can you telnet to the website using the ip and port 80?
eg. telnet 192.168.0.1 80

---

