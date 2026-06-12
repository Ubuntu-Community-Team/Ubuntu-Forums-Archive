---
title: "Setting up SSH-server: overcoming router"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by troyaner on 2008-11-06
How to get secure access to my pc, which is behind a couple of routers and an internet provider?

SHH is up and running, I tested it on the local network, now I would like to do so from anywhere via internet.
Do one need a static IP or something?

Running Ubuntu 8.04 (testing a couple of things and off to Intrepid! :D)

I would JFGI, if I knew, what to look for...

Thank You in advance!
Tr.

---

### Post by Matthileo on 2008-11-06
> **troyaner said:**
> How to get secure access to my pc, which is behind a couple of routers and an internet provider?

SHH is up and running, I tested it on the local network, now I would like to do so from anywhere via internet.
Do one need a static IP or something?

Running Ubuntu 8.04 (testing a couple of things and off to Intrepid! :D)

I would JFGI, if I knew, what to look for...

Thank You in advance!
Tr.

I havent set up a server, so take my advice with a grain of salt, but have you set up your router(s) for [port-forwarding]("http://en.wikipedia.org/wiki/Port_forwarding") on the port SSH uses?

If not this is probably why you can't access your server from the internet.

---

### Post by helgman on 2008-11-06
Like Matthileo, you might need to open the port in one (or more) firewalls/homerouters depending on the network layout. You also need to know your public IP to get to the machine. Try Wikipedia for more info about public/private IP:

[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

As for static IP - yes, it makes things a lot simpler (or you'll have to keep track of every time the public IP-address changes). One way to overcome the problem with changing dynamic IP is to use DynDNS or similar services ...

Guess we need more info (network design etc) if you need more help. ;)

Regards,
Helgman

---

### Post by superprash2003 on 2008-11-06
for ssh usually opening port 22 is required..you can find port forwarding information for your router here [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm) ...if you have dynamic ip as mentioned above you could use dyndns service..

---

### Post by troyaner on 2008-11-07
Thanks for your replies!!! :)

@Matthileo, helgman, superprash2003
For one of the routers is in another flat and is not even mine, there is no way (well... without making the owner nervous...) to interfere or open any other ports than the usual HTTP,FTP,POP3...
We (several students) share a DSL connection via local network (so I suppose, our WAN-IP would be the same), and I would like to access my on-line password-protected PC from anyone/anyone else.

@helgman, superprash2003
DynDNS seems interesting, would it be possible to go
```
ssh -X troyaner@troyaner.some-service.net
```
from elsewhere?

having no better idea I tried
```
ssh <my.ip>
```
but it didn't work, as I think mainly because I was adressing my internet provider, but not my sub-machine....

I have a little experience with local linux networks, but never went "beyond" our router and have only a general idea how DSL connections, DNS and routing work ;)

---

### Post by helgman on 2008-11-08
OK ... sounds a bit fishy but ...

As for connecting, yes, ssh -X [email]user@somedomain.net[/email] will work with DynDNS.

BUT ... you must make sure that you can reach port 22 all the way from the Internet and into you machine. SO if you are on a DSL-connection, sharing the same IP, you must make sure that 22 is pointing at YOUR machine! Most homerouters have a port-forward function where you say that "port x should be forwarded to IP a.b.c.d.

As for ssh -X user@ip ... well ... IP must be a public IP-address (note one specified as private in RFC 1918 or the wiki-page I posted earlier).

So, if you used IP 10.x.x.x or 172.16.x.x. (or anything from 16-32) or 192.168.x.x ... then you should not be able reach your machine via the Internet.

Regards,
Helgman

---

### Post by blackened on 2008-11-08
Simplest way would be to use Hamachi and create a VPN to tunnel into your server with.

---

### Post by troyaner on 2008-11-08
@Helgman: 
as I cannot do anything to the router, this would be a difficult option...

@blackened: 
Thanks for the search query! will try

---

### Post by rturner on 2008-11-08
I could be missing something, but it sounds like the person who owns the router in the separate flat had a DSL connection going into his router and you and your friends are sharing it (?).  Without port 22 being forwarded from his router to your machine, you can't ssh into your machine from outside.  If the DSL connection and the ISP's WAN ip address is coming into *your* router directly and his is just another access point, then forwarding port 22 from your router to your machine would work.

---

### Post by troyaner on 2008-11-08
@rturner:
the first is the case, I can manage neither the router, nor the DSL-connection.

There is an option in SSH to change the "listening" port. As HTTP (port 80) is open per default, could SSH work through it?

---

### Post by rturner on 2008-11-08
I don't see how that would work.  Say you have it listening on port 80 and you can ssh into your dyn-dyn address on port 80 (ssh domain.com:80?), there's still no forwarding on the remote router (port 80 *or* port 22) to tell that outside address that your machine has the ssh server running.  Aside from the vpn suggestion mentioned above, my inclination is that you either have to get the person in the other flat to open the port in his router, or you have to get a direct dsl connection to your own router.

---

### Post by kevdog on 2008-11-08
If you have no access to the router, then if you want to continue on this solution, you would need to setup a ssh server elsewhere (work, uni) etc. and then setup a reverse tunnel to your house.

---

### Post by blackened on 2008-11-08
You're seriously making this much harder than it needs to be. Install Hamachi on the server, create a vpn, install Hamachi on the client, join the vpn, then use whatever protocol you want to connect to the server through said vpn. I promise you it's dead simple and takes almost no time or effort.

---

