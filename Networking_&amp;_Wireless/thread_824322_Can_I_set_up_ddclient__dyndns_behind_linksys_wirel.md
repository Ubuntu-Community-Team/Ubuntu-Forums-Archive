---
title: "Can I set up ddclient / dyndns behind linksys wireless?"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by lngndvs on 2008-06-10
I have a wireless router (linksys wrt 54g) at home through which my all-purpose desktop server/workstation are connected to the internet.  The local IPs are 192.168.1.XXX, assigned dynamically.  My DSl connection seems to be static; I don't know whether this can be relied upon.

I want to be able to connect to my home machine from the internet, put a server on it, edit files using emacs, ssh at will, run various processes from remote points.  I know that the linksys wireless router can connect to dyndns and get a domain name.  

What I don't know is how to EITHER assign a machine name that will be recognized from outside the router, OR disable dyndns on the router and in that case run dyndns directly from the machine behind the router.

I assume this is possible, that perhaps I'll need to assign a port.  I am foggy about ports.

Can someone point the way?

Thank you,

Alan

---

### Post by jimv on 2008-06-10
The outside world cannot see your machines behind the router.  This is by design.  What you have to do is tell your router where to send incoming traffic.  This is called port forwarding.

So say you have a webserver up on one of your machines.  Well, you have to tell your router to send incoming traffic on port 80 to that machine.  In the case of SSH, you would forward port 22.  FTP is 21. 

The settings on the router will ask you for something like this:

External Port:  port on the router that will be getting traffic
IP Address: ip address of machine that you want that traffic routed to
Internal Port: port on the machine that should accept that traffic

---

### Post by superprash2003 on 2008-06-10
portforwarding through virtual server.. steps are similar [http://prash-babu.blogspot.com/2008/05/portforwarding-through-virtual-server.html](http://prash-babu.blogspot.com/2008/05/portforwarding-through-virtual-server.html)

---

