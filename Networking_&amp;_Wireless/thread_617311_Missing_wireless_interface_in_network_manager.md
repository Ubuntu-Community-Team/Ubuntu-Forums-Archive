---
title: "Missing wireless interface in network manager"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by Caezar on 2007-11-19
The Wireless Network Interface is missing from Network manager (see attached screenshot). This is probably because I messed up the /etc/network/interfaces file.

Could anyone tell me the original content of this file?

Thanks!

---

### Post by WernerBrandt on 2007-11-19
Always rename/copy original file first :P

> sudo cp /etc/network/interfaces.old 
or bak or org or whatever

Ok, now what is supposed to be in it;
In your case I think:

auto Lo
loopback lo

auto eth0
inet eth0 iface dhcp


Or something..
Look for something with # before it.
But my guess is that you are missing drivers...

---

### Post by 321on on 2007-11-19
Hi I've got exactly the same problem - sorry I can't help solve your problem.
How do I get drivers to a wireless PC with wt111 attached to it.  Have successful ping.

---

