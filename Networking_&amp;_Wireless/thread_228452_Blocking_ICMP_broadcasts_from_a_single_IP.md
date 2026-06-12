---
title: "Blocking ICMP broadcasts from a single IP"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by luca.b on 2006-08-03
Hello. I'm having a problem on this network, due to a probably zombie machine on it: since this morning I get this filling my kernel log:

```
[17185222.656000] 159.149.89.174 sent an invalid ICMP type 3, code 3 error to a broadcast: 159.149.89.255 on eth0
```

As I have no authority to locate or warn the user of that IP, how can I use Shorewall to stop this? I already have:

```

DROP            net:159.149.89.174      $FW
DROP            $FW     net:159.149.89.174

```

using the single-network interface setupm, but that doesn't yield any results.
Any hints on how to solve this? Thanks!

---

### Post by luca.b on 2006-08-03
Actually I found out it's an answer to the samba broadcasts I send. Still, they are annoying.

---

