---
title: "configuring intranet"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by ub007 on 2008-06-23
Hi,

I'm new to linux,had posted this thread in the beginners forum,but some of the guys suggest i post this here.so here it is-

I'm trying to setup an intranet within my university network for tesing and learning use.at the moment,i got 3 PCs and a switch.I've installed ubuntu server on one PC and this machine is connected to the internet.I intend to have the other 2 PCs(ubuntu again) to act as clients to the server.
-I would like to have the server lease out ip addresses to the 2 Desktops.(dhcp)
At the same time i do not want the server dhcp to mess up with the uni network.... 
Also need to ensure the clients access the server locally and not via the internet....
How do i configure the dns and dhcp(both client& server)to accomplish this?do i need to configure the switch as well or just plug the 3 comps into it...?or do i have to use the switch at all?...totally confused.....

Cheers
Davis

---

### Post by rogier.de.groot on 2008-06-23
Configure a switch? How? Why?
Anyway, go the help.ubuntu.com site, check the server docs, they explain how to set up DNS/DHCP. You shouldn't need to configure DNS/DHCP on the client; just tell 'em to use it.

---

### Post by ub007 on 2008-06-24
hi,

finally,i've now got my intranet up and running with a dhcp configured on my ubuntu server leasing out ips to the clients.
however,at the moment the n/w is isolated from the uni  n/w.(the 4 PCs,including the server r plugged into a switch) ...I cant figure out a way to simultaneously acces the internet via the uni network.Every time i wish to access the internet,i unplug the ethernet cable from the switch n plug into the real n/w and in /etc/network/interfaces(server)-change from static to dhcp....
Will it work if i use another PC as a router,but i do not know how to do it....
Any ideas..thanks in advance

---

### Post by rogier.de.groot on 2008-06-24
You want to use your server as a router? If so, it'll need two network cards (one for the switch that connects to the other pc's, one for the uni network). Change your DHCP config so your server is set as default gateway in the client PC's. Enable ip forwarding and masquerading (don't remember the specifics, just google).

---

