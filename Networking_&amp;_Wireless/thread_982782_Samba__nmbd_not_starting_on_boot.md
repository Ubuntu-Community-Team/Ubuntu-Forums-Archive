---
title: "Samba / nmbd not starting on boot"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by tritium6 on 2008-11-15
Hello! I'm having a problem with nmbd. It doesn't start when my system boots, but as soon as I ssh in, it starts right up with /etc/init.d/samba restart. The error message in nmbd.log is 

```

[2008/11/15 00:17:05, 0] nmbd/nmbd.c:main(697)
  Netbios nameserver version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/11/15 00:17:05, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
[2008/11/15 00:17:05, 0] nmbd/nmbd.c:main(771)
  ERROR: Failed when creating subnet lists. Exiting.

```

The money line (I think) is:

nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating.

But I have no idea what to do about it.

Any help is greatly appeciated. Thanks!

-Randy

---

