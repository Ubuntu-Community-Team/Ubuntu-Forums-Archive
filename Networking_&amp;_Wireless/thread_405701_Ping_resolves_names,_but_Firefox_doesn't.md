---
title: "Ping resolves names, but Firefox doesn't"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by ahickey on 2007-04-10
Hi,

I installed Ubuntu 6.10 64bit on a Asrock ALIVE NF6G-DVI with a wireless PCI (RT2561) card from [www.linuxemporium.co.uk](www.linuxemporium.co.uk)

After I do the following command I get an IP address from my wireless router and all looks right with the world.

sudo ifup ra0

But, the problem is if I ping a website address it resolves and I get a response, but if I try this in Firefox it fails.  Unless I ping the site first.

Effectively Firefox or any other application (Package Manager) cannot resolve IP address from names but Ping can.  Once Ping has resolved then the name/ip address resolution is available to other apps.

Any thoughts would be helpful

Albert.

---

### Post by teaker1s on 2007-04-10
DNS issue, if you either enter your ip as static and isp dns ip you should find that solves it, 

System>Administration>Networking

or dhcp
[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns]("http://www.ubuntuforums.org/showthread.php?t=282034&highlight=stabilise+dns")


failing that you may have ipv6 problem

---

### Post by ahickey on 2007-04-10
Thanks for the quick response.
I will try the DNS thing this evening as the problem is in the Package Manager as well as Firefox.

What I can't understand is how Ping resolves but FireFox or Package Manager do not.
I would expect it to be all or nothing.

Albert.

---

### Post by Wielenga on 2007-04-10
Had the same problems. Posted a solutions but in the wrong folder probably :-)

[http://ubuntuforums.org/showthread.php?t=405733]("http://ubuntuforums.org/showthread.php?t=405733")

---

