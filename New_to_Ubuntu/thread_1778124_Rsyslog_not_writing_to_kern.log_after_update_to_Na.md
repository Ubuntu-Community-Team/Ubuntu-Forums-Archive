---
title: "Rsyslog not writing to kern.log after update to Natty"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by Blond_Knight on 2011-06-08
I updated to Natty a couple days ago.  Ive got an iptables rule that "should" log everything to kern.log. Its always worked before.
> sudo iptables -A INPUT -j LOG

Now theres nothing going to kern.log.  Is anyone else having this problem?

---

### Post by Blond_Knight on 2011-06-08
Correction:  Apparently its logging the iptable logs to the screen.  Ive tried different log levels but theyre all going to the screen.

---

