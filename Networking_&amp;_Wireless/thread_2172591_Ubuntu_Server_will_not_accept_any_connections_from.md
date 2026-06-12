---
title: "Ubuntu Server will not accept any connections from outside LAN"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by S._C. on 2013-09-05
I'm not very experienced with Linux-derivative operating systems, so please excuse my lack of knowledge.

I'm running Ubuntu Server on an older machine I purchased from a salvage shop, and it will not accept any incoming network connections from outside the LAN.

The login banner identifies the OS as "Ubuntu 13.04 (GNU/Linux 3.8.0-19-generic x86_64)"

I can make connections to the server from machines inside the LAN, and it can connect to servers on the Inernet, but any attempt to access it via the router's external IP address or from another address do not succeed. I have forwarded the appropriate ports to the server on my router, and UFW says the firewall is disabled (I don't intend to run it at all times like that, but I disabled it to eliminate that variable). 

Does anyone have any ideas as to what's wrong, or additional diagnostic steps to try?

---

### Post by houstonbofh on 2013-09-05
Either;

Your router/firewall is not fully port forwarding.
or
Your server is restricted to local access only.

It might help if you told us what service you were trying to connect to, and what ports you opened.  Config files help as well.

---

### Post by S._C. on 2013-09-05
Well, it really ought to be forwarding properly, because I've forwarded ports to other machines before.

I've got SRCDS (Valve's game sever) running on ports 27005 through 27105, and I've got SSH on 22. Neither one works.

Which config files do you need, precisely?

---

### Post by scbingham on 2013-09-05
How are you trying to test if your external ip address is working? You won't be able to do that from inside your network.

---

### Post by S._C. on 2013-09-05
That's what people tell me, but it's always worked for me.

But I checked before from external addresses, and it didn't work then either (the server was running Debian then, same issue, installed Ubuntu to see if that would fix it). There's also a 'master server' that checks in with the game server software I'm trying to run, and it can't see it either. I'll get someone else to try to connect from an external address, but I'm pretty certain that's not the problem.

EDIT:

Apparently the guy I had check before had some sort of network problem on his end, 'cos I just had someone else try and it worked. Sorry for my dumb mistake. :P

---

### Post by scbingham on 2013-09-05
Wasn't your dumb mistake. :-)

I test my external ip by using my phone. I disconnect from my router's wifi, tether to my laptop & test it with my dynamic dns record using the phone data network; saves relying on someone else (& their mistakes).

---

