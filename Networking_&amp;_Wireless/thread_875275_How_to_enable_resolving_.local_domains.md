---
title: "How to enable resolving .local domains"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by MobiusNZ on 2008-07-30
Hi guys,

I've finally worked out the solution for this problem so I thought I would share it here.

If you have a managed network (ie you have a server and real DNS), it is quite common to have a .local domain name. For instance, my domain name I have set up at home is hol.net.local (which matches my internet facing domain of hol.net.nz). 

While windows machines all handle this fine, some distros of Linux struggle with this.

It turns out this is because of mDNS, part of Zeroconf. This thing is meant to set up a network automagically for non-technical people. Unfortunately, it is set up to create a .local domain, which clashes with your managed one.

So the simple solution, in the end is to edit **/etc/nsswitch.conf** and replace the following line:
```
hosts:     files mdns4_minimal [NOTFOUND=return] dns mdns4
```
with:
```
hosts:     files dns
```

No restart required, easy as that. Hope it helps

---

