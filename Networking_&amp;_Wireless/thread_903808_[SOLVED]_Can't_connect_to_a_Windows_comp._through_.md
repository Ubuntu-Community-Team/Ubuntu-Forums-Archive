---
title: "[SOLVED] Can't connect to a Windows comp. through RDP (remote desktop)."
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Predator106 on 2008-08-28
Hi, 

  I can't figure out why, but I can't connect to my windows computer through remote desktop. This is what I would like to use, my other window$ computer can connect to it just fine, but it is however not going off the IP but rather it's network name. The name of the computer (internally) is P4-SERVER, and it's IP (static) 192.168.2.1 .

I have tried using (in Ubuntu (Gnome)), Remote Desktop Viewer, and Terminal Server Client. I actually have no idea what the difference between them is, except the latter looks more professional, and the prior looks easier :).

This computer also has a username AND password on it, but like I said, it is not a problem with the other Windows computer. I believe it is running XP PRO, or a server edition of some kind. 

This is really annoying, and, seeing as remote desktop already works for non-linux, what is the point of me installing VNC, and then I have to setup the client on the other computer (the not mine one). That was a rhetorical question by the way.

Thanks.

---

### Post by HermanAB on 2008-08-28
First test connectivity using telnet:
$ telnet ipaddressofwinxppc 3389

The Win PC should answer.  If it doesn't then you have a routing or firewall problem.

If it works, then try rdesktop:
$ rdesktop -g 90% ipaddressofwinxppc

Cheers,

Herman

---

### Post by Predator106 on 2008-08-28
Welp, it times out...damn.... But that doesn't make any sense, it must be an Ubuntu firewall problem then(as in it is too strict or something)... How can I open it up?

What is the 3389 for, is it the port that RDP runs on, usually?

---

### Post by Predator106 on 2008-08-30
The thing is, I can ping the computer and get responses....

---

