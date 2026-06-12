---
title: "ssh local port forwarding through router"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by Gabriel_Brown on 2015-08-22
I am trying to host a server online, I have people connecting to my home ip and using port setup in my home router they are sent to a computer with DD-WRT router (computer 1) from here I want another computer on the internal network behind the 2nd router to be a DMZ (computer 2).  From there, the people connecting would be sent out of the DD-WRT router and into another computer through ssh (computer 3).  Is this possible, the port I'm using is 25565 and where would I put my firewall software?

OSs:
computer 1: DD-WRT router
computer 2: Ubuntu
computer 3: Debian

---

### Post by TheFu on 2015-08-22
Only 1 system can be "DMZ". For dd-wrt, that means all ports are forwarded to the DMZ and the router doesn't do any filtering. If you do that, there isn't any need for the router at all.  Last time I checked. I could be out of date. Haven't used "DMZ" mode since I was a noob in the mid-1990s.

If you don't use the DMZ, then you can forward different WAN ports to different internal servers running ssh.  I like to use port-translation for this - don't forget to use the ~/.ssh/config file on the client to make the different userids, non-default ports, and any desired settings for the specific ssh connection. No need to remember those things and all ssh-using-programs honor these settings.

Be certain to use different subnets unless all the servers are to be available by the clients.

BTW, I'm not certain I understood the text description of the network layout. Perhaps you could do some ASCII art or just use the **tree** cmd with directories and files to show it?  Can't tell how the 2nd router is connected - or the DMZ or really anything else from the text. It is ambiguous, unclear.

Where to put firewall?  On every box and every router. That is common practice. Block everything and only allow the minimal required access.

BTW - I hope you have a business internet connection. Even so (I have one with a /29), reselling hosting services is probably against the ToS. It is here.  If you manage all the services, then it is a gray area. For a residential connection, all of this is definitely against the ToS most places.

---

### Post by Gabriel_Brown on 2015-08-22
I drew this:  (sorry its a bit big)
[IMG]http://www.mediafire.com/convkey/ce4b/jjrrip2olco7jbczg.jpg[/IMG]
All I want to do is connect computer 2 to computer 3 and let computer 1 (dd-wrt) basically treat computer 3 as if it was computer 2.
Computer 1&2 are virtual machines run on virtual box.  There is a network option and I have both computer 1&2 under the same internal network

---

### Post by TheFu on 2015-08-22
I you want to forward a port from in interface to another in/out on Linux, use iptables and enable ip_forwarding (basically you turn the PC into a router) in sysctl. There are many dangers in doing this and it does NOT help security.  You seem to already have a few routers available, so I'm confused why another is needed. [http://www.cyberciti.biz/faq/linux-port-redirection-with-iptables/](http://www.cyberciti.biz/faq/linux-port-redirection-with-iptables/)

Would help to see IPs for all the internal networking too, BTW.

This appears to be a bad network design. Do you have other devices on the network? Where are they? What is the point of the DMZ? It seems useless and why the 2nd router at all?  Is dd-wrt running on a cheap router box or a PC? How many ethernet ports does each router and PC have? Is that the limiting factor?  A $15 switch can make life much easier, perhaps?

There used to be a website - ratemynetworkdiagram - but it is gone now. It had hundreds of network diagrams and looking through those is a great way to learn.  Perhaps the wayback machine has old copies? Doubtful. Nope. It has the pages, but not the diagrams.

Found this:  [http://www.conceptdraw.com/samples/network-diagram](http://www.conceptdraw.com/samples/network-diagram) which might give you some ideas. Following existing diagrams prevents some security risks. Why relearn things that were solved 30 yrs ago?  Network design is the first step in running secure services.

BTW - using virtualbox for any "production server" is a bad idea too, IMHO. Move to Xen or KVM. We've used both and prefer KVM since 2010. It is extremely capable, faster than commercial solutions and pretty easy to get started - especially if you are comfortable with ssh.

---

