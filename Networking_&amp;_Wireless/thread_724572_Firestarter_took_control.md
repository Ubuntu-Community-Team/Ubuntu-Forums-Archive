---
title: "Firestarter took control?"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by dingorunner on 2008-03-14
Hello everyone, Obviously firestarter did not take control, but there must be some config error since every time I log into Ubuntu I have to run FIrestarter and then click on the Stop firestarter option in order to Pidgin and aMule to connect correctly, otherwise I get Connection Regected on Pidgin and Kad; Firewalled on aMule. What's with that? Thanks for your time.

---

### Post by pytheas22 on 2008-03-15
Which ports do you have blocked via firestarter?  I don't have much experience with iptables/firewalls in Linux, but obviously you would want to make sure that the ports you need are open.  Pidgin may require numerous ports since it supports several protocols; don't know anything about aMule.

---

### Post by dingorunner on 2008-03-15
Thanks for answering my post, well, I allowed traffic from 5222 (Xmpp-Client) and 1863 (Msnp) using firestarter and I used the following commands in order to get aMule working:

iptables -A INPUT -p udp --dport 4665 -j ACCEPT
iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
iptables -A INPUT -p udp --dport 4672 -j ACCEPT

---

