---
title: "Ping works but pages does not load? :O"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by arcktos on 2008-03-17
I installed my wifi card(ENLWI-g) with help of  ndiswrapper correctly.(It worked on previous versions of Ubuntu) but then i installed it on 7.10 something weird is happening: i can ping all websites, i can telnet on my router, and even my mail, but no page is loading in firefox, i cant wget it also, WTF?

---

### Post by arvevans on 2008-03-17
If you can ping using the IP address:
[INDENT]ping 91.189.94.158[/INDENT]
Then your network access to the Internet is probably OK.

If you can ping using a URL:
[INDENT]ping ubuntu.com[/INDENT]
Then your DNS service for address translation is probably OK.

At this point, if the browser still does not work, I would download and re-install the browser program.

Arv
_._

---

### Post by arcktos on 2008-03-18
synaptic does not owrks to
i cannot wget google.pl

******* ****.

---

### Post by arvevans on 2008-03-25
If not solved yet, this could be either a firewall problem or a DNS server problem.

If you can do everything by numeric IP address, but not by text based URL, then I would first approach it as a DNS problem.  On a Terminal screen (the dreaded Command Line Interface/CLI) do a "man dig".  This will show you how to use dig to debug DNS problems.  You should also be able to 'ping' your DNS server by numeric IP address.

When you try to access anything using a text-type URL, your computer will first send the text-URL to your DNS server...which will return a numeric IP address that is the actual IP number for your request.  Once your computer has the numeric IP address it will then attempt to contact the desired URL using the numeric address.  Text type URL's only exist between your computer and your DNS server, and serve as an easy way to remember locations which might be hard to remember using just a number. If you do not have a DNS to translate textual URLs into numeric IP addresses, then you will not be able to access Internet entities using text-type URLs.  There is a network hierarchy of DNS servers, including Primary, Secondary, and sometimes Tertiary.  Each DNS server gets it's information by linking to a parent DNS server that is higher in the network architecture.

If the problem is not DNS related, then you will need to dig into any firewall and/or proxy service that may be between your computer (or inside your computer) and the Internet.

Hope this helps.

Arv
_._

---

### Post by chilinski on 2008-03-25
Generally, you will find your DNS servers listed in /etc/resolv.conf. 

If you use DHCP, however, /etc/resolv.conf gets overwritten each time. You can force your dns servers if you use DHCP by putting them in /etc/dhcp3/dhclient.conf.

---

### Post by stream303 on 2008-03-27
> **chilinski said:**
> You can force your dns servers if you use DHCP by putting them in /etc/dhcp3/dhclient.conf.

It might be even easier of you are using a router, to place your ISP's primary and backup DNS server addresses in the router's own setup page.  I used to edit dhclient.conf, but had access to my router, so I don't have to deal with it everytime I reinstall, etc.

If you don't know your ISP's dns addresses, I like using OpenDNS servers.  They can be found at the bottom right of their page:

[http://www.opendns.com/](http://www.opendns.com/)

---

