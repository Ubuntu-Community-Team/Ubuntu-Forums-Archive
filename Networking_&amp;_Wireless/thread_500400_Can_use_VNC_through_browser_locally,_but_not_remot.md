---
title: "Can use VNC through browser locally, but not remotely, and port is open"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by se2131 on 2007-07-13
I have a VNC server hosted on my computer, and I'm trying to set it up so that I can access it from anywhere with a browser. Here's the service I'm running:

x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800

Ok, so here's what works with this setup:

I can access the computer using a regular vncviewer client (a .exe file), with my external IP address (e.g. 65.636.244.151:5900, which is not my real IP, but just showing i'm not using 192.168.x.x)

I can also access the computer through a java-enabled browser from any computer on the network, using the 192.168.x.x:5800 in the URL

However, I can't type in 65.636.244.151:5800, it says "Page not found." I've checked my router settings and the port is opened there, and the results from nmap give me the following:

5800/tcp open  vnc-http
5900/tcp open  vnc

Any ideas on what I need to do?  Thanks in advance

---

### Post by Mr. C. on 2007-07-13
It appears your router is not completely supporting NAT loopback.  In general, you don't use your WAN IP on the LAN; this must be specially supported by the router.

Test your WAN IP connections using WAN IP address from the WAN, and LAN IP connections using LAN IP addresses on the LAN.

MrC

---

