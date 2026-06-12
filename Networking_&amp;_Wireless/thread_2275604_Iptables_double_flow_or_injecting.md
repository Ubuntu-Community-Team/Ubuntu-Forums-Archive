---
title: "Iptables double flow or injecting"
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by wrkilu on 2015-04-27
Hi,

I have problem with transparent Squid and Snort together on same router. Why ? because packets are captured by iptables and pushed to them. So if they work singly - they work, but together no. 

Packet to Squid are redirected in standard way by:
-t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT

Packets to Squid are redirected by:
-I FORWARD -p tcp --dport 80 -j QUEUE

.. and the problem is when traffic goes to this or this software it never goes then to the second.

My questions are:
1) do you have any idea how to solve this ?
2) is it any way to possibly turn on double flow in iptables ? (then I will do Squid take traffic in first flow and Snort take traffic in second flow)
3) or is it any way in iptables to take traffic from some table/chain and push it back to other table/chain ?

Regards

---

