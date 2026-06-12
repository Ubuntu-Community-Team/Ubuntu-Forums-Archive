---
title: "Can't connect to the internet using my router in bidge mode"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by Martinffx on 2007-12-27
okay, so i've just switched to ubuntu from windows and I can't connect to the internet using my router as a bridge. In windows I used to go to the network connections window and use the create a new connection wizard to set up a broardband connection which i would use to connect to the internet. How would set up a similar connection in ubuntu 7.10?

---

### Post by Jose Catre-Vandis on 2007-12-27
Are you sure you mean "bridge" as opposed to gateway?

If your router is serving up dhcp addresses, why hasn't ubuntu picked one up by default and automagically connected you to the internet through your router?

Are you wired or wireless? Depending on your wireless adapter you may have connection problems

Have a look in System>Administration>Network

and also in a terminal type "ifconfig" (no quotes) to see what connectivity you have

---

### Post by ajgreeny on 2007-12-27
Wireless or wired connection?  usually ubuntu will just connect to a wired router without any further action on your part, but wireless can be more difficult and it will not have been found at install time if the machine was not attached by wire or with the wireless adapter.

You may need to use the terminal and type ```
ifconfig up
``` and see what the output is, then come back again if needed.

---

### Post by mips on 2007-12-27
1. Why would you want to use a router in bridged mode? Just configure it with your username & password so it does the authentication instead of the pc. The just get a ip address via dhcp.

2. If you really have to use it in bridged mode then use PPPoE which I think is shite way of doing it.

---

