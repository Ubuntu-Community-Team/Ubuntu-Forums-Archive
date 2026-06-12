---
title: "Missing configuration for cgconfig.conf  and  cgrules.conf."
date: 2018-07-17
forum: Networking &amp; Wireless
---

### Post by smithbox on 2018-07-17
Hi all.
Since e couple of days I tray to configure cgroups v.1 on:
```

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial
```
```
uname -a
Linux robin-desktop 4.15.0-24-generic #26~16.04.1-Ubuntu SMP Fri Jun 15 14:35:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```
My aim is to get daemon cgroulesngd assign all services to different cgroups.
I,am gonna use module net_cls.
The only problem is content for both files:
- /etc/cgconfig.conf
- /etc/cgrules.conf
Would appreciate any kind of help, because I spend too much time to give it up now !

Regards
Mark.

---

