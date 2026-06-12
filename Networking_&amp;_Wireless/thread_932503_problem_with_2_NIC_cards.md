---
title: "problem with 2 NIC cards"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by tesla.coil on 2008-09-28
Hi guys i have 2 NIC card on one my system one is connected to the internet via eth0 and other nic card to the LAN via eth1 connected to another machine ( running on redhat) the prblm is when i try to ping to my local machine it says sendmsg:operation not permitted how do i resolve this prblm?it works fine on windows

---

### Post by alastair on 2008-09-28
A setup problem somewhere.

Open a terminal and get the output of :

1) ifconfig -a

2) route -n

3) cat /etc/hosts 

Is a firewall running at all?

Cheers,

Alastair

---

### Post by The Foz on 2008-11-19
Hi,

Did you resolve this problem?

I am getting something similar (ping: sendmsg: Operation not permitted) on my ppp0 interface.

---

