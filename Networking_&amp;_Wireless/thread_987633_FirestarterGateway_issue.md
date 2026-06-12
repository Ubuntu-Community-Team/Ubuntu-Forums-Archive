---
title: "Firestarter/Gateway issue?"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2008-11-19
I have a gateway machine setup to protect my servers from malicious internet traffic. (I essentially have everything blacklisted except for http/https, nfs, samba, dns, and ssh.) I can ping the servers from one another and I can also ping the internet from any one of the servers. The problem is, any other computer outside of the firewall (i.e. wifi clients, my dad's office comp) can't ping the server or get to network resources!

My network is organized like this:
(this may be confusing, it's easier than it seems).
FiOS modem - Wireless router (we'll call it Main)

The Xbox and the office computer connect via ethernet to the router.
Everything else on the network connects via a wireless link, in some form.

Then, in the server room (ahem, closet) :) :
Wireless router (client bridge, connects to main, we'll call it subnet) - Firestarter Gateway - switch - everything else.

MY firestarter machine is configured like this (A more in-depth view):
Client Bridge - Eth0 (192.168.2.144) - FIRESTARTER - eth1 (192.168.3.1) - switch - everything else

Does anybody know why I cannot ping through the firestarter machine to reach my servers?

---

### Post by rhcm123 on 2008-11-19
And btw, i set outbound traffic to permissive and it had no effect. (Just to be sure)

---

