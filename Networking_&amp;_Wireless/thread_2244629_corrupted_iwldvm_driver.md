---
title: "corrupted iwldvm driver"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by nathan_wolfe2 on 2014-09-17
I've been running Xubuntu 14.04. One day the wifi stopped working. I have pinpointed the problem to a driver that seems to have become corrupted.

On startup this message appears:
```
iwlwifi 0000:01:00.0: failed to load module iwldvm (error 256), is dynamic loading enabled?
```

So iwldvm can't be loaded at startup. When I run this command:
```
sudo modprobe iwldvm
```
I get this:
```
modprobe: ERROR: could not insert 'iwldvm': Input/output error
```

As far as I can tell iwldvm is corrupted. How can I fix this?

---

### Post by praseodym on 2014-09-17
Please check
```

grep iwl /etc/modprobe.d/*
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep iwl
```

---

### Post by nathan_wolfe2 on 2014-09-17
Inexplicably, the wifi started working again. As such I doubt any commands I currently run would be of use. If I have any problems I'll post.

---

