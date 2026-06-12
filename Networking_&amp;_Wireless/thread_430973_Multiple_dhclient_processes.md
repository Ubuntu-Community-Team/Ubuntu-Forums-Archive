---
title: "Multiple dhclient processes"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by tbriers on 2007-05-02
Hi all,

Since I have upgraded to feisty I have some issues with dhcp.  When I startup my system there are two dhclient processes.  1: dhclient and 2: dhclient3

The consequence of this is that my network interface gets "multiple" ip's.  I mean that in the middle of the day my ip might change, which it never should do at the university.  (In most cases this is not a problem but at the university I lose my connection and I have to login at their server agian.  Which is anoying.)

Does anybody have an idea where this comes from or how to resolve it.

Output from ps -aux | grep dhcl  :

dhcp      5177  0.0  0.1   2456  1244 ?        S    16:20   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
dhcp     17791  0.0  0.0   2456   852 ?        S<s  18:19   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

As you can see both processes use the same network interface which is really strange.

Any help is welcom

Greetz

Tom.

---

