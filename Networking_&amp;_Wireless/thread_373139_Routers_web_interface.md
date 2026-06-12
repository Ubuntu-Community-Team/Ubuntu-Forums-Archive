---
title: "Routers web interface"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by xadloki on 2007-02-28
Hello, this is probably something really simple that I don't know about since I'm new to linux... 
I have a few routers (Linksys WRT54GL, Comtrend CT-561 and Conceptronic C54APRA) and I'm trying to access their web interface to change a few settings but in no router I am able to get into it... In windows I just type the IP address and have access to all of them just fine. Currently the connection is working perfectly but I wan't to open a few ports so could anyone explain what is it that is stopping the interface from loading ? the login screen shows up but after that it just stays loading, maybe a port that I need to open in Ubuntu ?

---

### Post by Stephen Howard on 2007-03-01
Maybe try an alternate browser in order to eliminate the browser (or more likely a particular setting on the browser) as the problem.  If that doesn't work, I'm not sure what else to suggest.

---

### Post by xadloki on 2007-03-01
Well I tried, Firefox, Konquerer, Epiphany, Galeon, Opera and Mozilla and none of them was able to load the interface... :( any other suggestions ?

---

### Post by eXisor on 2007-03-01
Is the ubuntu machine using a wireless connection to the router?

Most router software has a setting to enable/disable admin from a wireless device (to prevent router hacking problems). Check this on your routers.

To answer your port question. Routers are commonly configurable to use http or https to provide web admin. Unless you've configured the routers to listen on some other port (unlikely), then you do not have a port problem.

I assume the router is providing dns and dhcp services to the network?

---

### Post by xadloki on 2007-03-01
No all of them are connected through ethernet cable. And the listening port is port 80, the router is providing me with dns and dchp though I have changed that to static. I mean everything works great, ports that i forwarded are working correctly and so connection speeds are at max but I just can't get into the web interface... ofcourse there's always telnet but I prefer to have both options.
Before Ubuntu I tried openSUSE and I had the exact same problem, after accepting the login with the correct user and password it will start loading and it doesn't move on from that point, if however I type the wrong password it will ask for it again...

---

### Post by netztier on 2007-03-01
> **xadloki said:**
> Hello, this is probably something really simple that I don't know about since I'm new to linux... 
I have a few routers (Linksys WRT54GL, Comtrend CT-561 and Conceptronic C54APRA) and I'm trying to access their web interface to change a few settings but in no router I am able to get into it... 

Hm.. I had a Linksys WAG54G ( Router with integrated 802.11g AccessPoint, 4 port switch and integrated ADSL modem instead of an "Ethernet WAN" port) for some time. Browsing it with Firefox from Ubuntu and Gentoo was painfully slow, but it worked somehow. It took ages to load the small pictures that made up the components of the GUI. In Windows, it was fast and normal...

I never figured out why - the router's integrated switch died one day and I threw it away.

best regards

Marc

---

### Post by xadloki on 2007-03-01
Well for me the WRT54GL is working alot better than the Conceptronic, even with the factory firmware it loads pages faster than anything I've seen with the conceptronic... I was thinking of putting another firmware but this one is working so good I think I'm not going to change atleast until I need IPv6

---

