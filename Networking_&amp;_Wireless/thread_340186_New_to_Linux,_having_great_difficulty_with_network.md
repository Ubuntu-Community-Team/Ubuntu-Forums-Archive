---
title: "New to Linux, having great difficulty with network connection"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by dravensbe on 2007-01-16
I'm having a lot of trouble with my home network connection. I've tried using two different routers. I've had some success with both, but after a while the connection stops working. I'm running Edgy on my PC as well as a Macbook, and my roommates are on Windows boxes.

The two routers I've tried: AOpen AOH-508 and Linksys BEFW11S4 ver.4

I've tried both a dynamic connection and a static IP. The dynamic works for a while before stopping (with no error message of any kind), and I haven't been able to get the static to work at all. My only suspicion is that my Azureus may be configured improperly, and is somehow causing some kind of IP conflict.

When I run ifconfig, the IP I'm given is from my ISP; although I'm wired through the router, it doesn't seem to be assigning me an IP.

Sorry that this is so vague; if anyone can suggest some things to try, or more information that could clarify the problem, it would be most appreciated.

---

### Post by Metaljaz on 2007-01-17
If you go into System>Administration>Networking
In network settings select the connection you
are using and then select properties. You should
there be able to enter your IP address manually.

---

### Post by sanone on 2007-01-17
What might also help is disabling devices that you don't use like the wired Ethernet connections.

---

