---
title: "nftables syntax query"
date: 2015-05-23
forum: Networking &amp; Wireless
---

### Post by The Cog on 2015-05-23
I am trying to configure a map/dict for use in the nat table. The idea is to have a map of address translations for fast lookup. I can do translations with individual lines like this:
```
nft add table nat
nft add chain nat output { type nat hook output priority 0 \; }
nft add chain nat input { type nat hook input priority 0 \; }
nft add rule nat output ip daddr 1.1.1.1 dnat 192.168.0.1
nft add rule nat output ip daddr 2.2.2.2 dnat 8.8.8.8
```
This works, verified with tcpdump. But I want to use a map/dict because my intended use will have thousands of translation entries, using pre/postrouting instead of input/output.
I tried making a map like this:
```
nft add map nat fakes { type ipv4_addr : ipv4_addr \; }
nft add element nat fakes { 1.1.1.1 : 192.168.0.1 }
nft add element nat fakes { 2.2.2.2 : 8.8.8.8 }
```
and also tried:
```
nft add map nat fakes { type ipv4_addr :  verdict\; }
nft add element nat fakes { 1.1.1.1 : dnat 192.168.0.1 }
nft add element nat fakes { 2.2.2.2 : dnat 8.8.8.8 }
```
but in neither case can I work out the syntax to use the map in a nat rule: **nft add rule nat output ???**.
Is it even possible to use a map for daddr -> dnat address like this?

---

### Post by The Cog on 2015-05-26
Bump. Nobody knows?

---

