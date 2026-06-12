---
title: "iptables - port forwarding"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by satimis on 2006-11-26
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64

Which file I have to check the policy of iptables to see;

- whether having forwarded port 25 to server?

$ sudo iptables -L```

Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/S YN tcpmss match 1400:1536 TCPMSS clamp to PMTU

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I need to enable forwarding port 25 to server

Which file contains "server name" ?

I suppose iptables is running;

$ dpkg -l | grep iptables```

ii  iptables                                         1.3.3-2ubuntu4              Linux kernel 2.4+ iptables administration to

```
Is there any other way to check?

TIA


B.R.
satimis

---

### Post by syadnom on 2008-03-04
bump bump bump!  google is playing dumb!  this doesnt seem like it would be that hard but nothing seems to work!

---

