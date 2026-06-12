---
title: "How do I configure dynamic routing / interfaces ?"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by jbt on 2007-12-04
Hi

I have a Dell Inspiron installed with Dells standard Feisty.

I'm trying to configure, so that I can automatically use the ethernet when its plugged in, or the wirless when not.

The Network manager is supposed to do this, but seems to require DHCP, and doesn't support decent wireless configuration, so I need to add settings to the /etc/network/interfaces file.

Once I have settings in  the file, then Network Manager refuses to do anything.

Is there some way I can configure the route so that it uses the wireless when present, and ethernet otherwise without having to ifup/ifdown ?

I've tried adding metrics to the route, but that still tries to use the ethernet when it is unplugged.

Any other suggestions ?

Thanks
JohnT

---

