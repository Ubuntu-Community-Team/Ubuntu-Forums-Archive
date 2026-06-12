---
title: "localhost does not resolve"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by vanstrien on 2007-06-11
Hi there.

I've got this odd problem where a normal user cannot resolve 'localhost'.  Root does it fine.  I just get a message, "ping: unknown host localhost". I've checked my hosts file as well as looked at various permissions in my etc directory.  Everything seems right.  This system was installed as 6.06 and then upgraded to 6.10.  I've compared it to a freshly installed 6.10 system running on a laptop and cannot find any differences of note.

The key bits out of my hosts file are:
```

127.0.0.1 localhost hemlock hemlock.vanstrien.net
127.0.1.1 hemlock hemlock.vanstrien.net
```

And my nsswitch.conf:
```
hosts:          files dns mdns
```

And my host.conf:
```
order hosts,bind
multi on
```

Any suggestions?  This seems like it should be a stupid-easy problem to fix, but for the life of me I can't track down the source.  

Michael

---

### Post by turinglabs on 2007-06-11
Did you check the permissions on the nsswitch.conf file? It should be world-readable. I had a similar problem on a 6.06 server where the nsswitch.conf file had perms of 600 for some reason.

---

### Post by vanstrien on 2007-06-11
That was it.  Thanks!

---

