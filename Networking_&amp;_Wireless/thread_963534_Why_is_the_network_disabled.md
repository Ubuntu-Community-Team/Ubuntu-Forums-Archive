---
title: "Why is the network disabled?"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by craiggale on 2008-10-30
```
craig@craig-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:64:72:79
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 mult
```


Can somebody please tell me why the network is showing as disabled?

---

### Post by PinkFloyd102489 on 2008-10-30
Try this:

```
sudo /etc/init.d/NetworkManager restart

```

---

