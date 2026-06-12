---
title: "Making yourself invisible on network"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by mr.propre on 2007-02-18
Hi,

Is it possible to make yourself invisible on your local network. I knew somebody who had a firewall on his windows PC and even a network sniffer like (look@LAN) didn't find him.

So I wonder if this also is possible for Ubunut linux.

Thanks in advance.

---

### Post by simonn on 2007-02-18
```

$ sudo iptables -P INPUT DROP

```

This will have to be run every time you boot, so add it, without the sudo, to /etc/rc.local.

---

