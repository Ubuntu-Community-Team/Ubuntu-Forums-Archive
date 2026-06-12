---
title: "BIND9 and Subdomain"
date: 2023-11-24
forum: Networking &amp; Wireless
---

### Post by chfloreck on 2023-11-24
Hi
I need to setup an subdomain in bind9.
And I can't get I running:
Here the Zonefile:
$ORIGIN darkwing.net.
$TTL 604800     ; 1 week
@                               IN SOA  dnsdcp.darkwing.net. admin.darkwing.net. (
                                145        ; serial
                                604800     ; refresh (1 week)
                                86400      ; retry (1 day)
                                2419200    ; expire (4 weeks)
                                604800     ; minimum (1 week)
                                )


@               IN              NS              dnsdcp.darkwing.net.


dnsdcp  IN              A               172.168.50.41


cluster-gns-vip         A       192.168.100.100
dnsdcp                  A       192.168.50.41
ISCSI                   A       192.168.50.45
ISCSI-SAN1              A       192.168.51.101
ISCSI-SAN2              A       192.168.51.102
LinuxWS                 A       192.168.50.50
NODE1                   A       192.168.100.111
NODE1-SAN               A       192.168.51.111
NODE2                   A       192.168.100.112
NODE2-PRIV              A       192.168.52.112
NODE2-SAN               A       192.168.51.112


If I setup this:


**$ORIGIN         clusterA.**
**@                                       IN      NS    gns.clusterA.**
**gns.clusterA.                   IN      A     192.168.100.100**

I run into this error:
Nov 24 22:30:28 dnsdcp.darkwing.net named[690]: /var/lib/bind/db.darkwing.net.zone:28: ignoring out-of-zone data (clusterA)
Nov 24 22:30:28 dnsdcp.darkwing.net named[690]: /var/lib/bind/db.darkwing.net.zone:29: ignoring out-of-zone data (gns.clusterA)
Nov 24 22:30:28 dnsdcp.darkwing.net named[690]: zone darkwing.net/IN: loaded serial 145




**$ORIGIN         clusterA.darkwing.net.**
**@                                       IN      NS    gns.clusterA.darkwing.net.**
**gns.clusterA.                   IN      A     192.168.100.100**

This reports this error:
Nov 24 22:33:10 dnsdcp.darkwing.net named[690]: /var/lib/bind/db.darkwing.net.zone:29: ignoring out-of-zone data (gns.clusterA)
Nov 24 22:33:10 dnsdcp.darkwing.net named[690]: zone darkwing.net/IN: clusterA.darkwing.net/NS 'gns.clusterA.darkwing.net' has no REQUIRED GLUE address records (A or AAAA)

Can You tell me, what's wrong?

Thanks a lot.
Christian

Update:
I changed it to:
**$ORIGIN         clusterA.darkwing.net.**
**@                                       IN      NS    gns.clusterA.darkwing.net.**
[B]gns.clusterA.darkwing.net.                      IN      A     192.168.100.100

[/B]Now, now errors come up.
But - is this a correct setup for an subdomain?

---

