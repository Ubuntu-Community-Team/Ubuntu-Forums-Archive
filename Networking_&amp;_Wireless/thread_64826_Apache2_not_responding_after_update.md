---
title: "Apache2 not responding after update"
date: 2005-09-12
forum: Networking &amp; Wireless
---

### Post by EmmAytch on 2005-09-12
Hi

I have a LAMP setup running moregroupware.  All was working well until I did a security upgrade (patches from long ago - but I only recently built the server).

It stopped working!  I can access apache by http://127.0.0.1  but not by the ip address of the pc ( http://10.0.1.1)

When going in through 127.0.0.1 - everything is there and working fine.

netstat -ant gives:

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN

I have disabled the firewall.  I have re-installed apache and php4

I just cannot get it to respond on 10.0.1.1  - I have even listed this specifically in ports.conf - but to no avail.

I am hoping someone else has had a similar experience.

It's probably something really obvious, but I can't see it!  ](*,)

---

