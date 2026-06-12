---
title: "iptables error"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by callmebadger on 2011-08-19
hi all

got this error
iptables -N whitelist
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Error inserting ip_tables (/lib/modules/2.6.32-33-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.4.4: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

help needed please

[http://ubuntuforums.org/showthread.php?t=1827290&page=2](http://ubuntuforums.org/showthread.php?t=1827290&page=2)

---

### Post by dave01945 on 2011-08-19
have you tried running the command with sudo thats what the permission denied means and i think iptables needs to be run with sudo


```
sudo iptable -N whitelist
```

---

### Post by callmebadger on 2011-08-19
Thank you

will give it a go.

dont know a thing about this OS :D

---

### Post by bodhi.zazen on 2011-08-19
Please do not start multiple threads on the same topic. I answered in your other thread and starting a new thread like this leads to duplication of effort.

---

