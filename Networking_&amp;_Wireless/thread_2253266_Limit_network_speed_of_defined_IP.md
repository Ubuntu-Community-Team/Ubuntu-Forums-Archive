---
title: "Limit network speed of defined IP"
date: 2014-11-18
forum: Networking &amp; Wireless
---

### Post by sitapea1337 on 2014-11-18
Hello!

Is it possible to limit speed of specific IP (destination or source - or both)?

I tried this, but it gives me an error "RTNETLINK answers: Operation not supported"

```
tc qdisc add dev eth0 root handle 1: htb
tc class add dev eth0 parent 1:0 classid 1:1 htb rate 500kbps
tc class add dev eth0 parent 1:0 classid 1:2 htb rate 500kbps
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src 192.168.1.2 flowid 1:1
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst 192.168.1.2 flowid 1:2

```


Thanks in advance,
sitapea1337

---

