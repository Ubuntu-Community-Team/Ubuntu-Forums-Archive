---
title: "Static Routes Through DHCP"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by kaffe_02 on 2008-09-09
I am trying to assign static routes using dhcp

Im setting this option on my dhcp server
```

option static-routes 10.0.0.1 192.168.1.2, 10.0.0.2 192.168.1.2;

```

And this seems to work fine for my windows users, but my ubuntu users aren't picking up these static routes.

**from my dhclient.conf**
Ive added a request for the static-routes option, but that doesn't seem to be getting it done for me.
```

request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope, static-routes;

```

Does anyone have any ideas I can try to get my ubuntu users to pick up the static routes from the dhcp server?

Thanks,

---

### Post by kaffe_02 on 2008-09-17
Bump,

Any ideas, Anyone?

---

