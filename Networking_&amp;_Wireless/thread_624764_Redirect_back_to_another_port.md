---
title: "Redirect back to another port"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by arsham on 2007-11-27
Hi there
I have to machines
laptop :  192.168.1.5
and a desktop : 192.168.1.10

I added a rule to desktop machines iptables , and I want to redirect every connection from 192.168.1.10:3000 to 192.168.1.5:80

I did this :

iptables -t nat -A PREROUTING  -p tcp --dport 3000 -j DNAT --to 192.168.1.5:80

Works from anywhere , but my own laptop ( redirection is to the laptop )
What is missing here?

Thanks
Arsham

---

