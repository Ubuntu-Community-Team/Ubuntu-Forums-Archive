---
title: "iptables -m connlimit"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by georg on 2006-09-03
I was wondering whether it's possible to use iptables connlimit (iplimit) match with packaged kernels at all or must one always do the patching and recompiling by themselves?

Currently there's /lib/iptables/libipt_connlimit.so module present in the system but no matching module in /lib/modules/*/kernel/net/ipv4/netfilter/ so I guess that's the reason why I get "iptables: No chain/target/match by that name" when entering for example:

> iptables -I INPUT -p tcp -m connlimit --connlimit-above 1024 -j REJECT

Any ideas anyone?

---

### Post by dario on 2006-09-14
Not any better than to [report in Launchpad]("https://launchpad.net/distros/ubuntu/+bug/60439") :(  as I just did.

---

