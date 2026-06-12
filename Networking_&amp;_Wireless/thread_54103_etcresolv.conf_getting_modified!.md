---
title: "/etc/resolv.conf getting modified!"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by adwait on 2005-08-03
Hello!

Well here's my problem. I configure resolv.conf for certain nameservers, but after some time it reverts back to having 
```
nameserver 192.168.1.1
```
in it.

This was fine when I was using my router, but now I have configure the router to work in Bridge mode, so that I can connect and disconnect using PPPoE in Ubuntu. So the proper name servers need to be there in the resolv.conf. Any idea why this is happening/what I can do?

Adwait

---

### Post by varunus on 2005-08-03
The GNOME networking tools modify resolv.conf.  Make sure that you have the correct nameservers there, and it should work.

You may also want to try "resolvconf" from synaptic; it's an automatic resolv.conf handler.  I'm using it so my resolv.conf file changes automatically when I connect to a VPN; I'm not sure if it can do what you want it to, but you could read up about it.

---

