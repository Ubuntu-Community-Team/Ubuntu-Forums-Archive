---
title: "TC only limits upload speed."
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by rpugsley on 2015-01-07
Hi there, 

I'm trying to configure a QoS to my enterprise.
This script only limits my upload speed, meanwhile download stills at full.

What's wrong?


```

#!/bin/bash

tc qdisc del dev eth4 root 

###################################################################################
#eth4 = INTERNET
#
###################################################################################
tc qdisc add dev eth4 root handle 1: htb default 10

tc class add dev eth4 parent 1: classid 1:1 htb rate 100mbit ceil 100mbit
tc class add dev eth4 parent 1:1 classid 1:10 htb rate 20mbit ceil 20mbit prio 1

tc qdisc add dev eth4 parent 1:10 handle 120: sfq perturb 10

tc filter add dev eth4 parent 1:0 protocol ip prio 1 handle 1 fw classid 1:10


```

---

