---
title: "Anyip feature across machines"
date: 2021-12-07
forum: Networking &amp; Wireless
---

### Post by seenutn on 2021-12-07
I was trying to use the anyip feature in ubuntu and it works great.  I was able to bind a whole subnet to the machine.  Now how to make that subnet reachable from other machine?

My first machine and sec machine are on the same subnet 10.100.0.0/16 with IP 10.100.209.24 and 10.100.181.110.  On my first machine I used anyip feature and bind a whole subnet to that machine (  ip -4 route add local 192.168.0.0/24 dev lo).  So I am able to ping 192.168.0.6 on the machine1 itself.

I added a static route on sec machine (  ip route add 192.168.0.0/24 via 10.100.209.24 dev ens5 ) but I am not able to ping anyip subnet (ping 192.168.0.6 on sec machine does not work).  

What am I doing I wrong?  How to make it work?

Regards,
Seenu.

FYI: I am using 20.04.3   (Linux ip-10-100-181-110 5.11.0-1020-aws #21~20.04.2-Ubuntu SMP Fri Oct 1 13:01:34 UTC 2021 aarch64 aarch64 aarch64 GNU/Linux)

---

### Post by seenutn on 2021-12-09
Hi,
   It worked.
   I was trying with instances of aws and had to switch off "src/destination check" in setting of each instance.

Regards,
Seenu.

---

