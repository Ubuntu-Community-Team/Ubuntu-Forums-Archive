---
title: "Very slow computer with high CPU usage"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by mistypotato on 2010-09-14
Hello,
I am running Ubuntu 8.10 on a server and I'm experiencing very slow conditions with very high CPU usage.

But when I look at the Processes, no file is listed that is using all that processing power?

Any idea where to start looking?

thx

---

### Post by dirty_harry on 2010-09-14
Collection of monitoring tools:
[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

**dstat **gives a good overview

 **atop** is also considered a bottle-neck-killer:
[http://linux.die.net/man/1/atop](http://linux.die.net/man/1/atop)

but with heavy load you might prefer to switch off accounting:
```
ATOPACCT="" atop
```---
what's the setup? any information?

---

