---
title: "Network help please."
date: 2005-04-07
forum: Networking &amp; Wireless
---

### Post by studentx on 2005-04-07
Please Help!  Installing hoary crashes when it tries to configure my network setttins, so I went into expert mode and skipped it.  Everything is good, except I don't know how to configure my network card now that I've installed hoary.  Can someone post instructions on how to do this please.  I use dhcp.

Any help is appreciated

-X

---

### Post by studentx on 2005-04-07
So I went and pulled the resolv.conf file from my suse partition, and I updated /etc/network/interfaces

auto eth1
iface eth1 inet dhcp

but when i try to login after i enter my password the system stalls.  I can use recovery mode and ping google, and i get a response though.  But i figured out i couldn't ping my hostname (the default ubuntu).  Does that have something to do with it?   :confused:

---

