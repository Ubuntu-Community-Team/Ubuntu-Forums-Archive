---
title: "IPv6 (6to4) not used by default"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by Parallel on 2008-06-10
I have set up a 6to4 tunnel in hardy using a script in /etc/network/if-up.d:

```

#!/bin/sh
echo $IFACE >> /tmp/IPV6DEBUG

if [ "$IFACE" != eth0 ]; then
	exit 0
fi

IPV4=`/sbin/ip -4 addr show dev eth0|grep "^ *inet"|sed -r -e 's:.*inet ([0-9\.]+)/.*:\1:'`
IPV4STRIP=`echo $IPV4 | tr "." " "`
IPV6=`printf "2002:%02x%02x:%02x%02x::1" $IPV4STRIP`

echo $IPV4 >> /tmp/IPV6DEBUG
echo $IPV4STRIP >> /tmp/IPV6DEBUG
echo $IPV6 >> /tmp/IPV6DEBUG

/sbin/ip tunnel add tun6to4 mode sit ttl 64 remote any local $IPV4 2>&1 >> /tmp/IPV6DEBUG
/sbin/ip link set dev tun6to4 up 2>&1 >> /tmp/IPV6DEBUG
/sbin/ip -6 addr add $IPV6/16 dev tun6to4 2>&1 >> /tmp/IPV6DEBUG
/sbin/ip -6 route add 2000::/3 via ::192.88.99.1 dev tun6to4 metric 1 2>&1 >> /tmp/IPV6DEBUG

```

And that works nicely, I can ping6 IPv6 sites, and i can browse IPv6 only sites (for example [ipv6.google.com](ipv6.google.com) and [www.ipv6.sixxs.net](www.ipv6.sixxs.net)).
But any site that has both IPv4 and IPv6 addresses ([www.kame.net](www.kame.net) or [www.sixxs.net](www.sixxs.net)) always uses IPv4.
I think this behavior changed sometime during spring (I tracked hardy since about christmas).
And I can't find any way bring back the old behavior. I have tried to editing /etc/gai.conf, recompile glibc (I suspected the local-ipv6-lookup.diff patch), but no matter what I try, nothing changes.

Anyone have any ideas?

---

