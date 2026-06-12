---
title: "Cannot connect to CUPS remotely"
date: 2015-01-27
forum: Networking &amp; Wireless
---

### Post by spookybathtub on 2015-01-27
I'm trying to connect to CUPS web interface from a remote machine over the internet.  Can't figure out what the problem is.  The debug log shows this error:
```
Request from "*hidden*" using invalid Host: field "*hidden:12345*"
```

I have these lines in cupsd.conf, so it should allow everything.  (I know this is not secure, it's just for testing right now.)

```
Listen 12345
Listen /var/run/cups/cups.sock

WebInterface Yes

<Location />
  Order allow,deny
  Allow all
</Location>

<Location /admin>
  Order allow,deny
  Allow all
</Location>

```

---

### Post by spookybathtub on 2015-01-28
Forgot to mention, the connection works over LAN, but not from an outside computer.  I have already forwarded the port on my router, and I think if the router was the problem, cupsd wouldn't be logging any error.

---

