---
title: "IP problem with local / public IP"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by thimo2 on 2014-04-08
Hello everyone,

Sorry for the bad title, I have no idea how to explain my problem.

I set up an Ubuntu server today, for my gameservers. My Ubuntu server is local, so it's hosted on a home network (The server will be private though, pure for testing mods). 
My local IP of my Ubuntu server is: 192.168.189.128. My public IP is: 77.172.xx.xxx. I do have a domain for my website, but now I want to host my website on my Ubuntu server.

So, I actually want to point my website's DNS to my Ubuntu server. I tried to enter my Public IP on the DNS A Record, but it redirects me to my router settings. 

I want it that my public IP > 77.172.xx.xxx redirects itself to the server's local IP (192.168.189.128) , and not my router local IP ([http://192.168.1.254/](http://192.168.1.254/))

So: website > 192.168.189.128. (I want my servers to use: example.com:28960)

Is this possible? Yes, how?

I tried: Port forwarding port 8080 and changed ; Listen 80 to ; Listen 8080. I portforwarded both 8080 and 80 port. 

I hope you guys can help me out. Thanks in advance,

Thimo

---

### Post by TheFu on 2014-04-09
External DNS must point to the public IP.
You'll need to forward any/all ports needed for the games internally on the router to the static IP of the server. You may or may not want to translate those ports.  I translate ssh from 61022 --> 22, as an example.
Some Netgear routers don't do port translation.

The router manages a local LAN.  99.9999% of the time, all the computers inside the network should be on that same subnet - so you probably want to re-IP your server to be 192.168.1.{something}.

---

