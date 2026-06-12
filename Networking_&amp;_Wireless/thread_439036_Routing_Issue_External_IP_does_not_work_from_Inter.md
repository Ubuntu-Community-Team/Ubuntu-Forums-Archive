---
title: "Routing Issue: External IP does not work from Internal Computer (LAN)"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by stormfrog on 2007-05-10
I have an issue with routing that I just cant seem to grasp. 

I have a Webserver on my Local Area Network. Its running fine and people can connect to it w/o any problem. Between LAN and WAN on my network there is a router that does all the routing. Its responsible for connections to the Webserver on the Lan among other things (that is, routing traffic to my External IP on port 80 to the Internal IP which belong to my webserver).

If I type my **Internal IP** of my Webserver in a browser on my **Local Computer**, my webserver sends me www-pages.

If I type my **External IP** of my Webserver in a browser on my **Local Computer**, no www-pages are loaded and I get a time-out error.

I have made a traceroute when I try to connect to my Webserver on the external IP. It only makes one hop and I believe that the connection I am attempting never leaves my router (it does not continue to my ISP and go back that is). If I set a proxy in my browser to "force" the connection to leave my router I get a working connection to my Webserver. So it is safe to safe this is a routing issue with my router. I have heard other people complaining about just this but none of us has the faintest idea how to proceed to solve it.

The routing rule I use to enable access to my Webserver is something like this:

Route WAN connections on port 80 to LAN on specific IP 192.168.1.1

Naturally I tried to route LAN connections on port 80 to webserver. But this doesnt work for some reason.

(*192.168.1.1 is my Webserver*)

I am clueless! If I were a king Id promise you half my kingdom and my daughter to the person who solved this, however since I am not I can atleast offer my gratitude! :)

---

### Post by ohgod on 2007-05-10
I'm thinking that your routing rule to foward requests from your WAN on port 80 to your webserver isn't going to apply to traffic originating from the LAN.

I'm a little confused though...If you know the webserver responds correctly when you use a proxy to force the traffic to go outside your network, then what's the problem?  In my opinion, loading your external IP from inside your network isn't all that important as long as you know it works from outside.  Or am I missing something?

---

### Post by stormfrog on 2007-05-10
Of course it is important! Good routing is what makes life worth living! :) 

For development óf www-services/projects/sites it is a problem since these often has script-data refering to extranal ip. Sure, I could use a proxy but I hate proxies and its not a solution, just avoiding the problem.

---

### Post by ohgod on 2007-05-10
Ahhh, I see.  Sorry, I'm just not used to writing web site code that needed to know the IP it was running on.

---

### Post by netztier on 2007-05-11
> **stormfrog said:**
> 
If I type my **Internal IP** of my Webserver in a browser on my **Local Computer**, my webserver sends me www-pages.

If I type my **External IP** of my Webserver in a browser on my **Local Computer**, no www-pages are loaded and I get a time-out error.


For a common router that does PAT for outgoing connections, this is standard behaviour: No "looping" connection may go through the firewall. Even enterprise-class devices such as the PIX or Firewall Services Module by Cisco forbid this: you can't connect to an (or the) external IP address from the inside. Period.

Solution: tweak name resolution in your LAN, so that a query for [www.yourdomain.com](www.yourdomain.com) returns the internal IP address of your web server.

Three ways to do this: 
[LIST]
[*]on all your internal computers, add and entry to **/etc/hosts** that matches the external name to your internal IP address.
[*]run a local DNS server that resolves your external name to your internal IP address
[*]use a Router/Firewall that can do "DNS forging" by intercepting the external DNS' reply packet and mangling your internal IP address into it.
[/LIST]

Best regards

Marc

---

### Post by stormfrog on 2007-05-22
adding my external domain to %systemroot%\system32\drivers\etc\hosts worked like a charm. Thanks!

---

