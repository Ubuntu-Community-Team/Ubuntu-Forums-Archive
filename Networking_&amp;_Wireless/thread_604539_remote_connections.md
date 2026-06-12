---
title: "remote connections"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by devilears on 2007-11-06
Is it possible to connect from a linux box on my company's LAN, to a desktop machine standing at my house 35km away? What do I need to accomplish this?  The machine at home is connected to the internet 24/7 via my Internet Provider.

---

### Post by spd106 on 2007-11-08
Sure, the most common secure method is to use SSH. [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

You will probably need to forward the connection through your firewall. This will be port 22 by default, though it's usually a good idea to move it to a different port.

NB Make sure you have a strong password on your home PC because it will be accessible to everyone on the Internet.

---

