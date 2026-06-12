---
title: "tc ingress doesn't work on ubuntu 16.04"
date: 2018-07-23
forum: Networking &amp; Wireless
---

### Post by zackliu on 2018-07-23
[COLOR=#242729][FONT=Arial]Don't know whether it's OK to post this thread here.

I used [/FONT][/COLOR]tc[COLOR=#242729][FONT=Arial] to limit the inbound bandwidth. It's limited but didn't keep consistent with what I set. 
[/FONT][/COLOR]tc qdisc add dev eth0 ingresstc filter add dev eth0  parent ffff: protocol ip u32 match ip src 0.0.0.0/0 police rate 10mbit burst 10m drop flowid :1[COLOR=#242729][FONT=Arial]
And at last, I got the download speed of 2-3KB/s. The speed never changed whether I change the [/FONT][/COLOR]rate[COLOR=#242729][FONT=Arial] or [/FONT][/COLOR]burst

---

