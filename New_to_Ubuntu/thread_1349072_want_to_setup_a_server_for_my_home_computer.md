---
title: "want to setup a server for my home computer"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by venkat24 on 2009-12-07
Hi All,
         I am new to ubuntu.I have installed ubuntu server edition but i want to make my home system dedicated as server through internet.Please help how should i configure the server something like venkat24.com  or through IP address.

Thanks in Advance.
Venkat

---

### Post by diablo75 on 2009-12-07
Well it depends on what you are wanting the server to do.  It could host HTTP, VNC, SSH, perhaps email (although I've never done that).  Whatever it is you plan to do with it, you'll need to make sure that computers on the Internet are able to easily access it.  If the computer is directly connected to the Internet, then all you would need (bare minimum) is the IP address of the machine.  But that address is assigned by your ISP and can changed on rare occasion, so you'd want to setup an account with [www.dyndns.org](www.dyndns.org).  I've never done this where the computer itself updates their servers, but there are tutorials out there... just hit google up for that.

If you're like most people, your computer is behind a router.  You'll want to setup your router to login to your dyndns account, update them on your Inet IP address, and then setup port forwarding on the router so inbound traffic on specific ports are fowarded on to your server.

---

