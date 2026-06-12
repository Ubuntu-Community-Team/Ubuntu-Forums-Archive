---
title: "How to store and use automount information in NIS/Yellow Pages?"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by davidkahn on 2007-09-20
I installed autofs and have automount working using /etc/auto.master /etc/auto.home to define configuration.  However, it would  be  easier to manage  the  network  if  we  could  store  the  automount  information  in  the  yellow pages.

I have edited /var/yp/Makefile to add compilation of auto.master and auto.home.  However, it hangs on creating the two yp databases.  I could read up on sed to figure out the correct format for the input files.  However, if it is already documented, I'd appreciate knowing what these two files should look like.

I would also like to know if in Feisty whether /etc/nsswitch.conf has any effect on automounts, as `info libc "Name Service Switch"'  talks about the automount database being a feature for the future.

Thanks.

David

---

