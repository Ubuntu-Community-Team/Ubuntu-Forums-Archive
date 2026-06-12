---
title: "Curious network problem"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by dr_jb on 2007-10-13
I am trying to share an internet connection thru my ubuntu desktop.  I am connected to the internet on the ubuntu machine with a wireless card (ath0).  I have a wired connection (eth0) between the ubuntu desktop and a windows pc.  Here is the problem...

Currently I am connected to the internet wirelessly. But I can't reach the net from the windows machine.  If I change the gateway on eth0 (it is currently blank) to the ip of ath0, I can ping/vnc between eth0 on ubuntu and windows, but 192.168.1.1 (my internet router) becomes unreachable on ath0.

Any ideas on how to remedy this?

---

### Post by spd106 on 2007-10-15
Have you set up NAT or a bridge?

I would recommend Firestarter for Internet Connection Sharing.
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

---

