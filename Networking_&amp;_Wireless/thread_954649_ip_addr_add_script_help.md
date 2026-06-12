---
title: "ip addr add script help"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by TuckLive on 2008-10-21
I'm trying to get the following script to work:

```
#!/bin/bash
#

for i in 'seq 10 254'; do sudo ip addr add 192.168.1.$i/24 brd + \
                                dev eth0; done
```

When I try to run it I get this error:

ERROR: an init prefix is expected rather than "192.168.1.seq"

What am I missing?

---

### Post by uljanow on 2008-10-21
```
for i in $(seq 10 254); do sudo ip addr add 192.168.1.$i/24 brd + \
                                dev eth0; done
```;)

---

### Post by TuckLive on 2008-10-21
Thanks, the script runs now, but I get this error now:

RTNETLINK: file exists

---

