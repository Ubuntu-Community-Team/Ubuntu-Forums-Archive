---
title: "proxy bypass SSH from XP to Ubuntu"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by ushills on 2007-10-08
Hi

At my company we have a proxy filter uses port 8080 on 10.6.1.161 to redirect traffic to the outside world.

I want to be able to use putty (on USB stick) to access my Ubuntu machine through SSH (currently using port 22), how can I use either internet explorers proxy locally on the machine to make it appear that the traffic is from IE.  Or bypass the proxy filter to say use an outgoing connection on 443 to connect to my machine.

I don't know if IT filter proxy access on application but I would imagine I could get around that my changing the program exe for putty to iexplore.exe

---

### Post by banditti on 2008-05-21
Try changing the port of your ssh server from 22 to 443.  Some proxies will only allow traffic out on 80 or 443.  Also, give your ssh server a dns address.  Some proxies will only allow you to go by name and not by ip.

---

