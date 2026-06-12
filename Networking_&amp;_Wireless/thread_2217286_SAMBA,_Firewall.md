---
title: "SAMBA, Firewall"
date: 2014-04-16
forum: Networking &amp; Wireless
---

### Post by swormuth on 2014-04-16
Greetings,

If someone could help me with a list of the terminal commands to add rules which will allow my local network devices unrestricted SAMBA access to each other, I'd really appreciate it.  The amount of information online gets rather confusing.

Basically, I want to allow all IP addresses on my local network (192.168.1.1) unrestricted access to each other for the purposes of file sharing, without exposing them to the outside world.  I would need to open all the necessary ports in UCF on the local side, like...

sudo ufw allow from 192.168.1.0/24 to any port 22

In the example above, would it be necessary to open Port 22 for the file sharing needs, and what other ports/commands should I use?

Thanks in advance,
Steve

---

### Post by ian-weisser on 2014-04-16
I'm confused. Shouldn't your router's firewall be protecting your LAN?

Do you really want to add such a complex set of firewall rules to every system on your LAN? Will you be able to maintain it?

---

### Post by swormuth on 2014-04-16
My router is protecting me to some degree, as routers do...  But it's only a handful of computers, so I want to enable the firewall and enable Samba within the LAN.  Not to mention, laptops travel to other wifi networks, so the firewall is important.

---

