---
title: "HELP ME fix error KISMET"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by ngoctuss on 2008-03-31
i don't  know, how does run kismet in ubuntu 7.10, when i run it, a messenger display


thiensa@thiensa:~$ kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
FATAL:  Unable to set up pidfile /var/run//kismet_server.pid, couldn't open for writing: Permission denied[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}


1/ every help me, is that meaning, ?
2/ how to configuation kismet.conf ?

---

### Post by PokerFacePenguin on 2008-04-01
> **ngoctuss said:**
> i don't  know, how does run kismet in ubuntu 7.10, when i run it, a messenger display


thiensa@thiensa:~$ kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
FATAL:  Unable to set up pidfile /var/run//kismet_server.pid, couldn't open for writing: Permission denied[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}


1/ every help me, is that meaning, ?
2/ how to configuation kismet.conf ?

Yes, you need to set your options in the kismet.conf file
There are alot of options in there you can set.  Make sure you know what 
chipset your wifi is using and then cross-reference the manual.

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

---

