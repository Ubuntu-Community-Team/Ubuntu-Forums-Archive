---
title: "Port changing ssh tunnel"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Mb0742 on 2008-05-12
Hey I was happy connecting to a host via ssh however due to Router changes the prots have become unusable. How do I connect out on another port

I was always using ssh -ND 23 [email]lol@somehost.org[/email]

But now it won't connect how do I get it through other ports?

---

### Post by Monicker on 2008-05-12
Specify the remote port with the -p option.


ssh --help

---

### Post by Mb0742 on 2008-05-13
So 

ssh -ND 23 -P 80 [email]lol@somewhere.org[/email]
?

---

### Post by tribaal on 2008-05-13
Your remote ssh server has to be listening on that port for it to work.

You need to add a "port #" line to your distant sshd_config file (where # is the port number you wish to use).

In your case, you'll need to add "Port 80", then restart the ssh service.

After than, "ssh -ND localhost:23 -p 80 [email]lol@somewhere.org[/email]" should work.
Mind that localhost:23 binds the socks proxy to your localhost on port 23, and only allows access from localhost. Then socks forwards whatever you send it to your distant server using port 80.

Hope this helps :)

- Trib'

PS: We are not discussing circumventing a firewall here I guess, since I'm pretty sure you know it is against the forum's code of conduct... Don't you?

---

### Post by Mb0742 on 2008-05-13
Yeah 100% we're talking about the host changing here ;)

---

