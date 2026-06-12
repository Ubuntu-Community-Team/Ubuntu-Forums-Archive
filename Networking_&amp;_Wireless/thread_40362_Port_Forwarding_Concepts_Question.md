---
title: "Port Forwarding Concepts Question"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by cwaldbieser on 2005-06-08
I am trying to teach myself about port forwarding on Linux, but I am running into some trouble getting anything to work.  I conducted the following experiment:

My home network consists of 2 machine-- my Ubuntu machine and a Win98 machine.  The Ubuntu machine's ethernet card is plugged directly into my router, which is plugged into my DSL modem.  The Win98 machine has a wireless USB adapter that connects it to the router.  On my internal network, the router is 192.168.0.1, the Ubuntu machine's eth0 interface is 192.168.0.2, and the Win98 machine's interface has address 192.168.0.3.

I wanted to see if I could forward port 80 on my Ubuntu machine to a well known web server.  I entered so iptables commands that were supposed to 1) forward the port 80 traffic from the Ubuntu machine to the Internet web site, and 2) tell the Ubuntu machine to accept traffic on port 80.   I also ran

$ sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

to enable port forwarding.

I then brought up a browser on the Win98 machine and entered:

[http://192.168.0.2/](http://192.168.0.2/)

in the URL bar.  The connection just timed out after a while, so I figure I was not successful.  

Is this experiment feasible with the physical connection I have set up?  Is there some way I can diagnose what's going on?

---

