---
title: "Avahi resolution unreliable"
date: 2022-08-03
forum: Networking &amp; Wireless
---

### Post by carmiac on 2022-08-03
I have two computers, one running Ubuntu Desktop 20.04, the other running Ubuntu Server 20.04, lets call them desktop and server. I have installed avahi-daemon on them both. Desktop is a development station, while server is a fresh install with little installed past the defaults.


From desktop, avahi-browse shows several things on the network, including printers, cell phones, etc. However, it does not show server. If I restart the avahi-daemon on server I can resolve server.local for a minute or two, but then it stops resolving. Also, if I run avahi-resolve-host-name server.local on the server I can resolve server.local from desktop for a minute or two. I am maintaining a ssh connection to server the whole time, so I know it is still on the wifi.


From server, avahi-browse shows nothing, and I cannot resolve any .local device, other than server.local. 


How do I make it so that I can reliably resolve server.local?

---

### Post by TheFu on 2022-08-03
Use DNS and static IPs.
Avahi is the wrong answer.

---

