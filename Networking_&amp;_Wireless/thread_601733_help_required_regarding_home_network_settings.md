---
title: "help required regarding home network settings"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by gdp77 on 2007-11-03
Hi. This is my home network :

[[IMG]http://img502.imageshack.us/img502/5265/testnv2.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img502.imageshack.us/img502/5265/testnv2.f995b9d104.jpg[/IMG]](http://g.imageshack.us/g.php?h=502&i=testnv2.jpg)


How must I setup PC1 and PC2 in order to have internet connection?

Thank u.

P.S. I use ubuntu 7.10

---

### Post by kevdog on 2007-11-03
Do you want static or dynamic IP addresses?  If dynamic, which machine is handing out the dhcp addresses?  Are there any other potential dhcp servers located on the other machines?

---

### Post by AlanSmithee on 2007-11-03
The first thing to realize is that the given the layout you have chosen "server" must also act as a router - it must be the "default gateway" for PC1 and PC2, and should have a default route pointing towards "router".  I guess you want "server" to act as a firewall and that is why you haven't got all four devices (router, server, PC1 and PC2) plugged into the switch?

---

### Post by gdp77 on 2007-11-03
> Do you want static or dynamic IP addresses?

I want static.

> I guess you want "server" to act as a firewall and that is why you haven't got all four devices

yes.

P.S. : the router in the pic is actually my adsl modem.

---

