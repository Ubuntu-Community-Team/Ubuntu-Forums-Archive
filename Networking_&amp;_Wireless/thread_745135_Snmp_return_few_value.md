---
title: "Snmp return few value"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by gbiondi on 2008-04-04
Hi,
I get few information from my snmpd installed on ubuntu 7.10 versus CentOS installation.
Anyone known the cause? snmpd.conf are equal on either installation..

Read this.. the first is a Ubuntu machine the 10.12.14.25 is a CentOS 5 installation..

root@gbiondi-desktop:~# snmpwalk -Os -c public -v 1 localhost | wc
1408 5902 66620

root@gbiondi-desktop:~# snmpwalk -Os -c public -v 1 10.12.14.25 | wc
2141 8866 106235

All the best

---

