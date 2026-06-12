---
title: "iptables can't initialise"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by sekrof on 2008-11-09
Hi,

I was wondering whether anyone has seen or could kindly throw some light on an issue I've encountered with my setup of iptables.

Server Details:

```

root@server:/etc# lsb_release -d -s -c
Ubuntu 6.06 LTS
dapper

```
```

root@server:/etc# uname -a
Linux ds6496 2.6.22-8-server #1 SMP Thu Jul 12 16:28:57 GMT 2007 i686 GNU/Linux

```

when I enter:

```

root@server:/etc# iptables -L -v

```

I receive:

```

FATAL: Could not load /lib/modules/2.6.22-8-server/modules.dep: No such file or directory
iptables v1.3.3: can't initialize iptables table `filter': iptables who? (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

```

I've been searching around for a few days, but have yet to find any solutions to what might be wrong.

From my own investigation the error is certainly correct in that 
[FONT="System"]/lib/modules/2.6.22-8-server/modules.dep[/FONT] doesn't exist.

As this is a new server (to me at least), could it mean that something has been missed on it's initial setup?  or does is mean something is simply broken?

All views appreciated.

Regards

---

