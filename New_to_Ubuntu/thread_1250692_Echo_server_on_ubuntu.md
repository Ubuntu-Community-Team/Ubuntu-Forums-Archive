---
title: "Echo server on ubuntu"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by miku82 on 2009-08-26
Hey,
is there a echo server (most os's apparently should have this) on port 7. I tried telnet, no connect, and searched through the repo's and didn't find anything. This server should just return everything is gets.

---

### Post by andrewc6l on 2009-08-27
I believe this is built-in (but disabled) if you have inetd or possibly xinetd installed. "Regular" Ubuntu doesn't normally ship with inetd for security reasons, but you can install it and tweak the config file to allow echo.

If you just want an echo server and not all the other things that x/inetd bring, there are lots around. Here's one in C:
[http://www.paulgriffiths.net/program/c/echoserv.php](http://www.paulgriffiths.net/program/c/echoserv.php)

Pretty much any tutorial for programming TCP/IP will have one - it's usually the second or third example :-)

---

