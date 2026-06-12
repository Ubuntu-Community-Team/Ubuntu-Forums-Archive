---
title: "NFS issue after client crash"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by _Franck_ on 2006-11-16
Our network has a bunch of Ubuntu 6.06 clients which mount /home at boot time from a FreeBSD 6.1 NFS server.

When a client crashes it won't mount /home at boot. In that case, trying to mount manually gives "can not read super bloc".

The client still appears in the "showmount" output of the server.

Sometimes /home will be mounted after the second reboot but sometimes not even after several reboots (I haven't been able to find a regular pattern here). If I restart the NFS server or just wait long enough (e.g. one day) everything is OK.

Is this a server or a client issue?
Is this related to the client still showing up in showmount?
Is there a better workaround than restarting the NFS server?

Regards,
Franck

---

