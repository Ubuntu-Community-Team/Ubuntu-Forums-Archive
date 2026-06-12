---
title: "Bizarre issue w/ netgear router"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by merkinftw on 2008-04-14
I am using a compaq v2000 laptop running gutsy that has no problem connecting to any wireless router except the netgear one at my local dennys.  I have personally reset this router myself, and i know it works because i am posting this via an itouch that is connected to it. My box sees the router, and when i try to connect, the grren light on the bottom of the connecting icon comes on, but the top one never does and the attempt just times out. Any ideas?

Many thanks in advance!!!

---

### Post by Red-Shield on 2008-04-14
can you ping it ?  can you talk to it at all remotely ?   mabey it has the max number of users ?  what about doing it in the terminal manually **sudo iwconfig eth0 essid "name of the network"**   then run sudo dhclient -r and last dhclient

---

