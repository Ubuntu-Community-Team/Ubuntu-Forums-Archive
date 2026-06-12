---
title: "tc command using rsvp filter"
date: 2014-07-28
forum: Networking &amp; Wireless
---

### Post by dharm2 on 2014-07-28
Hi,

I have been trying to use the tc command based on a manual that is already available. It worked fine with u32 classifier but with rsvp im getting the following error. Can anybody give suggestions on this in case i hav missed out on something??

tc qdisc add dev eth0 root handle 1: htb default 20
tc class add dev eth0 parent 1: classid 1:1 htb rate 2mbit burst 15k
tc class add dev eth0 parent 1:1 classid 1:10 htb rate 1mbit
tc class add dev eth0 parent 1:1 classid 1:20 htb rate 1mbit
tc qdisc add dev eth0 parent 1:10 handle 10: pfifo
 tc qdisc add dev eth0 parent 1:20 handle 20: tbf rate 20kbit buffer 1600 limit 3000
tc filter add dev eth0 parent 10:0 protocol ip prio 1 rsvp ipproto tcp session 198.168.10.64

[B]RTNETLINK answers: Invalid argument
We have an error talking to the kernel
[/B]

---

