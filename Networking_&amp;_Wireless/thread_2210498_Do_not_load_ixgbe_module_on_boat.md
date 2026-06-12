---
title: "Do not load ixgbe module on boat"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by yoave on 2014-03-11
Hi,

I'm running Ubuntu 12.04 and I'd like to blacklist ixge driver from being loaded on boot.
I've added to '/etc/modprobe.d/blacklist.conf':
"blacklist ixgbe"

BUT, it didn't work.

what am I doing wrong?

---

### Post by Hadaka on 2014-03-11
Hi, this may help,, you will need to load ETHTOOL
to configure the driver for linux.
[http://docs.oracle.com/cd/E19254-01/820-7895-11/z400033c1304933.html#scrolltoc](http://docs.oracle.com/cd/E19254-01/820-7895-11/z400033c1304933.html#scrolltoc)
fancy orcl stuff

---

### Post by chili555 on 2014-03-11
After a fresh reboot, before you do anything else, please show us:```
cat /etc/modprobe.d/blacklist.conf
lsmod
```

---

