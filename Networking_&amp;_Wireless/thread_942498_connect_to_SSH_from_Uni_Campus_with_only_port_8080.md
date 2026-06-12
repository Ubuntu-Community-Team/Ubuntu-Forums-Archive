---
title: "connect to SSH from Uni Campus with only port 8080 available"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by mrblonde1369 on 2008-10-09
hello! i've been searching the forum for a solution to my problem but couldn't find any, so here i am writing what i would like to solve.

i've set up an Openssh server at home (italy) on port 8443; i know it works because i've tested it hundreds of times from dozens of different computer when i was in italy.
now i'm in UK and i'm connected to internet through the university campus network; i've been trying for a few days to connect to my server in italy but can't find a way to do it.

i usually used putty or directly the console, but here nothing works.
the IT section told me that only port 8080 is open and so i've tried to find a way to tell my ssh client to use port 8080 to connect to port 8443 of my server, but no luck.

after different configs of putty (local tunnel, remote tunnel etc...) and different options of the ssh command (-L 8080:localhost:8443 my.server.com -p 8443, and other dozens of different combinations), i really don't know what to do.

can anyone please help me? thank you in advance

---

### Post by yogensha on 2008-10-10
There's no way you can connect to port 8443 on your server if you can only create outbound connections to port 8080.  The tunneling feature of SSH only does anything if you can connect to the server successfully.  It sounds like you need to change the port that your server listens on.

---

### Post by jimbojones on 2008-10-10
Anyone know if it is possible to use iptables to redirect ssh -p 8443 to port 8080 ......or would that packet still end up on port 8080 on the far end?

---

### Post by bukwirm on 2008-10-10
It's kind of strange that your IT deprtment would block outgoing connections... That is what you think is happening, correct?

Have you tried connecting to your server normally? (ssh username@server -p 8443)

---

### Post by mrblonde1369 on 2008-10-11
> **yogensha said:**
> There's no way you can connect to port 8443 on your server if you can only create outbound connections to port 8080.  The tunneling feature of SSH only does anything if you can connect to the server successfully.  It sounds like you need to change the port that your server listens on.

so you think that i should change the server listening port to 8080 since i only have port 8080 open for outbound connection here on my client? can't i just configure my client to use port 8080 to connect to port 8443?

if the problem is just that i have to change the listening port of my server to 8080 i can go into an internet cafe and in 30 seconds i can connect to my server and change everything. but can someone assure me this will work? thanks to everyone for the quick replies

---

### Post by kevdog on 2008-10-11
Although strange it does sound like the Uni is blocking outgoing ports.  It really depends on how their firewall packet filter is setup, since with a properly configured firewall you can block packets based on packet port source or destination.  I don't know the way your uni has configured their firewall, and neither do you.  I guess the safest way to set up your client and server would be to forward local 8080 port to the remote 8080 port on the server.  That way neither the source or destination port could possibly be blocked.  Either that or you will need to experiment -- and then you will discover whether the source/destination or both port rules are being blocked.

---

