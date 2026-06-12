---
title: "Very slow wired internet, but wi-fi and Windows are fine"
date: 2022-11-13
forum: Networking &amp; Wireless
---

### Post by SamInside on 2022-11-13
DNS stuff.

---

### Post by TheFu on 2022-11-16
Check the resolved.conf file.  Perhaps the desired primary upstream DNS isn't there?

```
[Resolve]
#DNS=
#FallbackDNS=
```

You probably want 8.8.8.8 and 8.4.4.8 if you don't mind Google's DNS spying.  After making any changes to that file, restart the daemon/service.

> 
The more they overthink the plumbing, the easier it is to stop up the drain.
-Scotty
IMHO, systemd being involved with configuring the resolv.conf file is crazy.

---

### Post by praseodym on 2022-11-19
What NIC is that?
```

lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
```

---

### Post by TheFu on 2022-11-19
> **praseodym said:**
> What NIC is that?
```

lspci -nnk | grep -iA2 net
ifconfig -a
lsmod
```

If he can ping 8.8.8.8, the NIC and the LAN network and the WAN network aren't the issue.  That leaves DNS.

BTW, nslookup and ifconfig are both deprecated.  
'dig' is the replacement for nslookup
and
'ip addr' is the replacement for ifconfig.  The ifconfig tools haven't been maintained since 2011 and work purely by luck.

---

