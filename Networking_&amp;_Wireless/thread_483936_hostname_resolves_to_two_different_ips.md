---
title: "hostname resolves to two different ips"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by nofrak on 2007-06-25
I'm running ubuntu 7.04 with lamp and kde.  When accessing the server from the local network, everything works fine, but when I try to access from an outside network, it times out.  I've also noticed that my hostname resolves to alternating ips: the static one I set up, and the last one assigned by dhcp before I set up the static IP.  

Thanks for any help you can give.

---

### Post by nofrak on 2007-06-26
Not to bump myself, but I've noticed something else odd.  When I connect from an external network that's very close (a wireless in the same building, but from a different source than the lan), it will connect, but only slowly.  After the initial connection, however, it speeds up considerably.  Anybody got anything?

---

### Post by kevdog on 2007-06-26
I would assign the LAMP server a static IP address (if not done), and then if behind a router, make sure you port forward at least port 80 to the static IP address (may need more ports).  You might want to power down and then power up the router if you can.

---

### Post by nofrak on 2007-06-27
Thanks for the response.  I'm on a static IP, so that's not the problem.  We're in an office within a university, so I don't have direct access to the router, but since I can access the server from a wireless connection, on a different network, I don't think that's the issue.

---

