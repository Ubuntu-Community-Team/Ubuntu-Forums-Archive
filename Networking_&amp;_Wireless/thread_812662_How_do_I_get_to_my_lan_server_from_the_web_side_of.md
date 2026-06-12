---
title: "How do I get to my lan server from the web side of the router?"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by habuchas on 2008-05-30
Here is where I am at present.  My lan consists or 2 wireless laptops and one desktop, all running windows and a older machine with Ubuntu server running. I have several instances of web pages running on the server in separate directories.  I have assigned a static 192.168.0.107 to the server.  The router is a linksys WRT54GS.  I can get to any of the web pages from any of my computers on my lan using the 192.168.0.107/~account.  I want to connect to the server from the 'net'.  I have a DynDNS which keeps track of my URL and I have set up port forwarding (3333 to 3333) on the router to point to to the server (192.168.0.107).  However I can not get to the account using the DynDNS URL.  
What do I have to setup on the server so the server can respond to an external ping or request for a web page?
I have read everything I could find and several times have screwed up the server trying some things to a point of having to rebuild the server twice.  It was a fun experience but didn't solve my problem.  Maybe it is age, I am 74 and probably too old to play with ubuntu but it is fun and frustrating at the same time.  Any assistance (not too cryptic) would be appreciated.
habuchas.......

---

### Post by tigerplug on 2008-05-30
Hey, 

You need to forward port 80 top route all incoming TCP requests on that port to the LAN ip address of the server.


Heres a guide on how to do that for your router:
[http://www.portforward.com/english/routers/port_forwarding/Linksys/WRT54GS/Apache.htm](http://www.portforward.com/english/routers/port_forwarding/Linksys/WRT54GS/Apache.htm)


Get that done first and if you have any more questions just PM me.


Cheers, 


Tigerplug

---

