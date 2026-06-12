---
title: "Ipv6 autoconfigure just doesn't work"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by growse on 2007-04-14
Does anyone know why the autoconfiguration for ipv6 in ubuntu (6.10) appears to be completely broken? It works for my gentoo and debian hosts, but my ubuntu hosts refuse to autoconfigure their addresses from the router (cisco 837).

For the record:

```

cat sys/net/ipv6/conf/default/accept_ra
1

cat sys/net/ipv6/conf/eth0.2/accept_ra
1

```

Ideas?

---

### Post by nautilus on 2007-04-15
router adverts are only ipv6's way of doing arp, in the context of that particular variable as i understand it.

you should also enable autoconf in that same spot:

echo 1 > /proc/sys/net/ipv6/conf/default/autoconf
echo 1 > /proc/sys/net/ipv6/conf/all/autoconf

(sysctl.conf style)

net.ipv6.conf.default.autoconf=1

this should help, i think, probably, maybe.

---

