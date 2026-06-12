---
title: "help getting wireless to work"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by craiggale on 2008-10-24
how do i stop my wireless from showing as "DISABLED"?


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

The problem occours when using kernel version 2.6.27.2 ultimate.  The same wirless connection works fine using the old kernel 2.6.14.2.

Same code with old kernel:

```
craig@craig-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
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
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

```

please help

---

