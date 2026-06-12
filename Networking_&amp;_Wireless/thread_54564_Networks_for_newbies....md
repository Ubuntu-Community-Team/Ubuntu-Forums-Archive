---
title: "Networks for newbies..."
date: 2005-08-05
forum: Networking &amp; Wireless
---

### Post by xmastree on 2005-08-05
I'm not sure if this is the correct forum, but here goes anyway...
Mods, feel free to move it if it's not.

I'm trying to set up a server, ultimately It will be a router/firewall setup. It's a PIII 500, with two NICs.

I set up the NICs such that eth0 is set to DHCP, and eth1 is static. I connected eth0 to my incoming broadband and I could connect to the internet.

I then tried connecting eth1 to this computer, which I changed to static ip but I couldn't even ping the other one, or telnet to it. The cable's fine (crossover) I've connected to the net through it.

Is it possible to simply connect two boxes with static ips and ping one from the other? 

Where's the howto for setting up a router? I couldn't find one.

---

### Post by nocturn on 2005-08-05
[QUOTE=xmastree]
Is it possible to simply connect two boxes with static ips and ping one from the other? 

Where's the howto for setting up a router? I couldn't find one.[/QUOTE]

Did you connect a single cable between the two?
If so, that won't work.  You either need a HUB/switch to plug them in or use a cross cable.

---

### Post by xmastree on 2005-08-05
[QUOTE=xmastree]The cable's fine (crossover) I've[/QUOTE]
Yeah, it's a cross cable. I made it myself, and tested it with the thingy which connects my wi fi.

Since I only have one monitor between the two, is there a way I can connect the two NICs together on the one unit and sent data back and forth, just to test things out?

---

