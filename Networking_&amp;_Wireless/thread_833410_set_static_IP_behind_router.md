---
title: "set static IP behind router"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by pickarooney on 2008-06-18
I usually let my router assign IP addresses to my PC and laptop via DHCP/DNS/whateverit'scalled and they normally get addresses .10 and .11. Recently though they've been getting random addresses on startup and so prt forwarding and ssh bookmarks get messed up.
What's the easiest way of forcing a static IP to the two machines?

---

### Post by Kebabman on 2008-06-18
The easiest and best way is to configure the IP addresses statically on your router. If you don't fancy this you can setup static addresses by editing the '/etc/network/interfaces' file. There is an explanation of how to do this in this thread :

[http://ubuntuforums.org/showthread.php?t=751117](http://ubuntuforums.org/showthread.php?t=751117)

---

