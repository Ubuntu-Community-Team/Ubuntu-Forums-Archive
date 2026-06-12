---
title: "Wireless needs configuration at every start-up"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by ChristianSolli on 2008-08-15
Hello everybody. After having many problems with my windows system I finally have installed Ubuntu 8.0.4 on my computer. There are, however, a few small thing I wonder, and hope someone know (and have time to) answer:

1) I have a desktop with a PCI wireless D-Link adapter. When I installed Ubuntu I went to the network utility to connect to a wireless network. It did, however, not come up any visible networks. If I manually enter the name of my wireless network + the password, I have internet (I'm writing here now). But I know that there are many networks here, and they used to all come up on my windows system (I have not made it invisible in any way).

2) Now I have to go into system-->administration-->networks every time I start the computer and repeat the procedure in order to have a functioning internet connection. Of course I want this to be automatic at start-up. Do anyone know how this is done?

3) I followed the trouble shooting procedure and I noted that it seems Ubuntu identifies the PCI-card as "Ra-link" instead of D-link. Could this be a reason?

Regards, Christian Solli, Trondheim, Norway

---

### Post by Ptero-4 on 2008-08-15
D-link must be the brand and Ralink the chipset in it (linux sees the chipset, not the name of the wireless card maker). Also have you tried leaving it in roaming mode (in system>administration>networks)? It should make all networks appear. Or you might want to use wicd instead (for some people it works better than networkmanager).

---

### Post by ChristianSolli on 2008-08-16
Thanks, it seems to be working better now!:)

---

