---
title: "Bonding: primary_reselect failure doesn't work"
date: 2017-12-08
forum: Networking &amp; Wireless
---

### Post by sasha777 on 2017-12-08
[FONT=verdana]Hello. Ubuntu 14.04.1 LTS x64, bonding driver 3.7.1, bonding in active-backup mode. Option primary_reselect failure doesn't work as expected - primary interface becomes active immediately after its link is restored. Command [FONT=courier new]cat /proc/net/bonding/bond0[/FONT] displays that primary_reselect failure is set, displays e.g. 1 faiure on primary interface and 0 failures on [/FONT]the other, but primary became active again anyway!?!

We also tried with updelay 200 (miimon is 100) but it didn't help. Primary_reselect better works fine. We need to use that machine in a real-time system, so we need to avoid flapping and unnecessary swapping of active interface. Thanks and best regards.

---

