---
title: "pidof deluge?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-05-01
It look like something have changed from 9.10 to 10.04 regarding deluge, when using 'pidof -x deluge' in 9.10 did I get the pid but that wont happen in 10.04. After looking in 'System Monitor' did I notice that there is no 'deluge' running but there is a '/usr/bin/deluge' question is how I get the pid from it, since 'pidof -x /usr/bin/deluge' wont work.

---

### Post by -humanaut- on 2010-05-01
try ps --help ps -A will display all process with PID's

---

### Post by quinnten83 on 2010-05-01
```
top | grep deluge
``` or ```
ps | grep deluge
```.

---

