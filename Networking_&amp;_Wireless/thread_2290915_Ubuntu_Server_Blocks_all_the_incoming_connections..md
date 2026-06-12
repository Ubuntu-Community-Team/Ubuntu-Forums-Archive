---
title: "Ubuntu Server Blocks all the incoming connections."
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by gidonyou on 2015-08-16
Hello, I have setup my VM ubuntu server and real machine ubuntu server. However, they seems like blocking all the incoming connection, I can install the programs fine, which proofs it isn't network problem. I have attached screenshots from VM Server.

Incase your wondering, I haven't configured anything, it is just a fresh installed computer.

[ATTACH=CONFIG]263879[/ATTACH]
Firewall Status

[ATTACH=CONFIG]263880[/ATTACH]
ping to google.com

[ATTACH=CONFIG]263881[/ATTACH]
ifconfig
[ATTACH=CONFIG]263883[/ATTACH]

ping from windows.. VM host computer.

Thanks for your kind assistant.

EDIT 1: Have I mentioned that I am using _ubuntu server 14.04.3_?

---

### Post by gidonyou on 2015-08-16
Okay, I realized that real machine server was working fine and VM it self needed port-forwarding, and it worked fine.

---

