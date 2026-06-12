---
title: "Router will not pass port 27015 to game PC server"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by pappo on 2005-05-17
I initially posted this thread under Hoary/gaming forum but then I thought this may be more of a networking question, than a gaming one.  Here is the original post:

========================================================
I am running Hoary and I created a dedicated server for CounterStrike Source.

I can see the CS server from my other PC's on the home lan, but I my son could not see the server (port 27015) until I made the Ubuntu server a DMZ, on my DLink router.

I am using a cable modem, into a DLink router which acts as my gateway (192.160.0.1).

I don't want to keep my Ubuntu server a DMZ because it will always be seen by the internet.

Does anyone know why Ubuntu is denying access to the 27015 port from my router/gateway when it is not designated as a DMZ, but is allowing access to the port from any other computer on my home (192.168.0.X) network ?

I am not running DHCP.   All four home PC's have a static IP.
The network consists of the Ubuntu machine, two WinXP's, and one Win2000Pro machines.

Thanks.
Phil

---

### Post by dave9191 on 2005-05-17
Is the router configured to forward traffic on that port to the gaming server IP?

---

### Post by pappo on 2005-05-17
Thanks for the quick reply.

Yes, the port is forwarded also.

My DLink router has an option for setting up a "Virtual server" and assigning particular ports, UDP and TCP, to that server.

I setup 27015 UDP and TCP on the Virtual Server.
If I make my XP box (192.168.0.112)  the CS Server, I do not have to do anything with the router DMZ setting.

But when the Ubuntu box (192.168.0.113 ) is the server, unless I tell the router to assign as a DMZ, it will not accept packets from my son's machine which is coming from the Internet.

---

### Post by dave9191 on 2005-05-17
Thats strange :( Im running a machine running ubuntu as a web / ssh server and all i had to do was forward the ports to the server machine and it works.

---

