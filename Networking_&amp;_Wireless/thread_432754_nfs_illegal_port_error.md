---
title: "nfs illegal port error?"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Elif Tymes on 2007-05-04
Hey,

I'm trying to set up my nfs so that I can read it from work, here is my exports file...

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/home/data/ 192.168.2.0/255.255.255.0(rw,sync)
/home/data/ 69.41.14.130(ro,sync)

```

When I mount it from my home network, it runs like a dream, NFS makes me so happy ;)

But when I get to work, and try to mount (after unmounting the home one) it gives me the following error:

```
mountd[26461]: refused mount request from 69.41.14.130 for /home/data (/home/data): illegal port 2695
```

Any hints?

---

### Post by Elif Tymes on 2007-05-04
Anyone?

---

### Post by rover_orna on 2007-05-06
try "insecure" option in the line where you've got the export for work, so it'll accept connections from ports >1024 (at work you are probably behind masquerade).

---

