---
title: "trouble resolving FQDNs"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by jman623 on 2007-06-19
I've been trying to get ubuntu to join our active directory domain by following this tutorial:

[http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)


however it can't seem to resolve the FQDN of our domain controller

and when i try to ping it, it can't seem find it, but if i ping it by it's IP it works just fine.

here is the configuration for nsswtich.conf
```
passwd:         compat winbind
group:          compat winbind
shadow:         compat
hosts:          files dns wins
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis
```

here is my resolv.conf file:
```

search OLSOnlineDM


nameserver 192.168.11.176
nameserver 192.168.11.175
```

Help would be much appreciated :-)

---

### Post by jman623 on 2007-06-19
ok I was able to resolve the FQDN of the DC by adding the hosts file but now when I try to iniatiate kerboros I get this error:

```

kinit(v5): Cannot resolve network address for KDC in requested realm while getting initial credentials

```

---

