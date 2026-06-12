---
title: "How to use remote desktop?"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by Hayesio on 2008-03-28
Hi guys,

I have a friend whom I have resently converted to Ubuntu and he is having a few configeration problems - nothing serious - and i can fix them.  The only problem is that he lives in a different city.  I want to use remote desktop access to configure his pc. I have asked him to turn on the Remote Desktop options and he has done that.  When I type" vncviewer <ip address>" it responds with this:
```
VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

```
Can somebody tell me what i am doing wrong? how do i use this function?

My friend has a dsl modem connected directly to his pc, no router.
I dont have a router either.
And i can ping the my friends ip address.

Thanx

---

### Post by kpsmith on 2008-03-28
It would appear that his vnc server is not accepting your connection, is he running a firewall or anything that would no allow the connection?

You will also need to setup port forwarding on his router to forward traffic on ports 5800 and 5900 to his local machines IP address. If he has a dynamic public address then it would be worth setting up a dyndns account for him so that you don't have to guess the address to connect to everytime you connect or it changes.

---

