---
title: "connecting to my server from outside my network"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by porteclefs on 2008-10-28
Ok, so my server has a static ip.
My server is behind a router, so I've set my router to rout the ports I want to connect on to my server.

What else do I need to do? and how do I find out what ip address to navigate to when trying to connect to my server from outside my LAN.

---

### Post by nixscripter on 2008-10-28
Whatever IP address your router has on the outside of the LAN is what you connect to on the outside. Your computer will see the connection from the outside IP as if that computer were inside your lan connecting directly.

A bit longer explaination: let's say A is your computer, B is your router, C is the machine on the outside. B the router has an IP of 10.0.0.1 on the inside of your LAN, and an IP of 69.69.69.40 on the outside of your lan. C is outside with 204.204.204.22, and A is inside with 10.0.0.3. C connects to 69.69.69.40, and will get access to A. A will see an incoming connection from 204.204.204.22. In other words, the router will hide the two IPs it translates in between.

---

### Post by porteclefs on 2008-10-29
> Whatever IP address your router has on the outside of the LAN is what you connect to on the outside.

I understand this. I should have been more clear. How do I find out what ip address my router has on the outside?

thanks

---

### Post by PinkFloyd102489 on 2008-10-29
[http://whatismyip.com]("http://whatismyip.com")


It would also be a smart idea to set up a free dynamic domain, such as one from DynDNS.org. That way all you have to remember is the domain name. And if you have a capable router (such as Linksys), you can set up the router to automatically update the IP address to which the domain points. That way you will NEVER have to remember the IP.

Btw, this is how I have my server set up and it rocks. :P

---

### Post by porteclefs on 2008-10-29
ok, let me ask you this. I'm sitting behind a router which is behind a DSL Modem that also is a router... I think this is causing me problems.

I the server is connected to the router which is connected to the modem/router which is connected to the phone jack... 

I'm guessing that my WAN IP is the modem/router. So, do i need to set up forwarding of that to my other router (the router to which all of my network computers are connected) and then have that router rout specific ports to my server?

---

### Post by porteclefs on 2008-11-03
any one??

---

### Post by jimv2000 on 2008-11-03
If you're sitting on a computer connected to that router, just go to [http://www.whatismyip.com](http://www.whatismyip.com)

That will show you the external IP address of the router.

---

