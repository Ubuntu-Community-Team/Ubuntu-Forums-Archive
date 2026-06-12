---
title: "Adding Ubuntu Machine to network kills all internet connectivity"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by JMV290 on 2008-08-19
The other night I set up my aunt's wireless network which I'll also be using once I move in.  It was working fine until I connected the desktop running Ubuntu directly to the router via ethernet and the devices connected wireless lost all internet connectivity.

The current set up is:

Westell Proline DSL Modem > Linksys  WRT54G2 Wireless Router > Macbook Pro(Static IP), iPhone (DHCP), and a HP Notebook PC Running Vista(DHCP).

Does anyone know of a reason that adding the Desktop to the network would cause the other computers to lose their connectivity to the internet?

---

### Post by JMV290 on 2008-08-20
Bump.

---

### Post by cariboo on 2008-08-20
I can't see it killing all internet access, but check the ip addresses to make sure there are no duplicates. I have the same router and I have 1 dual boot vista/intrepid, 1 single boot windows xp, 2 Ubuntu servers, 1 Mac G3, 1 hp laptop Linux Mint wireless, 1 windows 2000, 1 dsl linux and a web cam with builtin web server all hooked up and working. Once in a while dhcp will assign the same ip address to two computers and that seems to cause the network to stop working.

Jim

---

### Post by JMV290 on 2008-08-20
> **cariboo907 said:**
> I can't see it killing all internet access, but check the ip addresses to make sure there are no duplicates. I have the same router and I have 1 dual boot vista/intrepid, 1 single boot windows xp, 2 Ubuntu servers, 1 Mac G3, 1 hp laptop Linux Mint wireless, 1 windows 2000, 1 dsl linux and a web cam with builtin web server all hooked up and working. Once in a while dhcp will assign the same ip address to two computers and that seems to cause the network to stop working.

Jim
I tried again last night and it worked so I'm going to guess that is what happened the other night.

Now i just need to figure out why the computer keeps freezing and seems to have a graphics issue.

---

