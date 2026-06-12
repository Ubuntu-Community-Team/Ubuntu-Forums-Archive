---
title: "Cups &amp; Dynamic IPs"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by c.dric on 2007-01-11
hey, 

my wireless network uses dynamic ips because it looks like my router/ap (airport express) doesn't support static ips. the problem is that when the (cupsd) computer gets a new ip, the other computers can't connect to the printer anymore.

the way it is setup now: in each other computers (xubuntu & osx) the default printer is configured as an ipp address in cups. 

i've found that you can also choose on of the published printers without the need to configure a printer with an ip but the downside is that those printers can't be used as default (at least in my test) and my users really need a default printer ready to print.

any advices for me ? :-k 
thanks.

---

### Post by c.dric on 2007-01-11
no cups gurus around ? 
:neutral:

---

### Post by c.dric on 2007-01-12
last try :)

---

### Post by spd106 on 2007-01-12
Are you absolutely sure that you can't give the printer a static IP address. As long as it's in the same subnet it should work, making sure that it isn't in the DHCP address pool.

E.g. Here I have an address pool of 192.168.0.3 - 192.168.0.30 and put the printer on 192.168.0.50. All with a subnet mask of 255.255.255.0.

I've not used an airport express, but it would be daft for this to any different and I would lose all respect for Apple.

---

