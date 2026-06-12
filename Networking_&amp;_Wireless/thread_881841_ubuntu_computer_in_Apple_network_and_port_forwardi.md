---
title: "ubuntu computer in Apple network and port forwarding"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by parkereagerton on 2008-08-06
I have an Apple Time Capsule with numerous computers networked. Most of them are Apples but I have one PC and one Ubuntu machine (a Dell Vostro). I want to allow someone to log onto the Ubuntu machine using VNC. I need to forward port 5900 and I need to tell the router what I am doing, I believe. It has to know where to send the data (which computer on the network). I have posted to forums before and gotten responses that though I was grateful for , did not help, as they assumed I knew a lot about Linux. The truth is I don't. I need step by step instructions if soemone has the patience.

---

### Post by komputes on 2009-07-18
The Apple Time capsule, being a proprietary tool, uses Universal Plug and Play (UPnP) and NAT Port Mapping Protocol (NAT-PMP) to "simplify" the process of starting servers on your computer and the router being smart enough to do the port forwarding for you. Apart from being questionably insecure (IMO), this protocol draft (not an accepted standard) introduced by Apple Computer as an alternative to the IGD protocol.

Sadly, I think you will need a Mac to make this change using the following instructions:
[http://must-know-mac.blogspot.com/2008/07/how-to-port-forward-time-capsule.html](http://must-know-mac.blogspot.com/2008/07/how-to-port-forward-time-capsule.html)

There is also an obscure project which has not been packaged for Ubuntu yet:
[http://miniupnp.free.fr/](http://miniupnp.free.fr/)
[http://miniupnp.tuxfamily.org/](http://miniupnp.tuxfamily.org/)

Bug to get this packaged for Ubuntu:
[https://bugs.edge.launchpad.net/ubuntu/+bug/313642](https://bugs.edge.launchpad.net/ubuntu/+bug/313642)

If you have a launchpad account, please mark this bug as affecting you and comment on the bug. If you are willing to test and compile the miniupnp project follow the instructions at [http://miniupnp.free.fr/files/](http://miniupnp.free.fr/files/) for linux. I would recommend doing this on a test machine or a virtual machine as I am not sure of the quality of this project.

---

### Post by komputes on 2009-07-18
I would like to make a correction; miniupnpd is a UPnP and NAT-PMP traversal daemon.  Apples' AirPort and TimeCapsule run such a daemon too, not miniupnpd though. Therefore this project will not allow you to admin your Apple router. from what I can see you either need a mac (well you need one to set  it up first anyhow) or you can use some applications that speak UPnP and NAT-PMP. Since there is no web interface to admin the router I do not think we have any luck but to use a mac for the config. This stinks of vendor lock-in.

:( Boo mac.

---

