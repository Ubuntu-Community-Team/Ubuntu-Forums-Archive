---
title: "Name resolution order"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by SimonHickling on 2008-10-10
I've set up a new server, and I have forwarded some ports from my router to the new server.  My DNS is all sorted with my DNS provider, and I can access the server from the internet.

I have also set both the FQDN and local name in the hosts file.  But when I run ```
host *FQDN*
``` locally it returns the external IP address.  If I ```
ping *FQDN*
``` it resolves to the local address.  I am having a problem with port access at the moment, and I think it's down to the addresses that some services are listening on, so I could do with it resolving to the local address, locally.

All help gratefully received.

Thanks

Simon

---

