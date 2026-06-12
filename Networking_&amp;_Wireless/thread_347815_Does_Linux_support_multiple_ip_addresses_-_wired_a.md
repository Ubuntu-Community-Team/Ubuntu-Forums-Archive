---
title: "Does Linux support multiple ip addresses - wired and wireless"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by robertpolson on 2007-01-27
Does Linux support multiple ip addresses ? Is it possible to have simultanious connection to both a wired router and another wireless router.

I need to have this:

Wired connection to a router for SAMBA file sharing and Internet access.

Wireless connection to ANOTHER router for SAMBA file sharing only.

Is this possible ?

Can one folder have one same samba config and be shared on both wired and wireless ?

---

### Post by RandomJoe on 2007-01-27
Sure, you can do that fine.  Each of the connections must be in a different network segment (say, wireless connects to a 192.168.0.x network, while wired is 192.168.1.x.)  Then you add a "default route" for the network that carries Internet access, so the machine knows to route all other IP traffic through the gateway on that network.

That probably reads like Greek to a lot of people... :D

---

### Post by robertpolson on 2007-01-27
Can you please elaborate on this "Then you add a "default route"

I am a noob coming from windows.

---

### Post by RandomJoe on 2007-01-27
I think this is one occasion where the GUI is the easy answer! :D

If you go System -> Administration -> Networking, when the Network Settings window opens, right at the bottom you will see "Default gateway device:" - Just be sure it's set to the appropriate network interface, and that should take care of it.

In more detail, you have to have a default route (even in Windows) to let the networking system know where to forward packets for IPs it can't get directly to.  So on Linux, a command line would be something like:
```
route add default gw 192.168.1.1
```
If you just run 'route' in a terminal, you will see one line that starts with 'default' which shows the current active route.  All packets with external IPs get sent to that gateway IP for handling.

---

