---
title: "Dans Guardian and Squid blocking e-mail and aptitude"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by greymoose58 on 2007-09-22
Actually, I'm not sure that it is DG or Squid, it might be the way I've configured our home network. 

We use a proxy server running Dapper, Squid, Dans Guardian, Apache2.0 and MySQL. Somehow one computer (family) can only connect through the proxy (which is fine - actually the whole idea) while the other  machine can go around it. The family machine cannot down load e-mails via pop3 or use aptitude to do updates. The really weird thing is that the other computer can do both regardless of using the proxy or not.

I suspect that I've blocked some ports I shouldn't have somewhere. Problem is I don't know which ports and I can't see where to change them anyway. Probably in squid.conf?

Any suggestions much appreciated.

Cheers.

---

