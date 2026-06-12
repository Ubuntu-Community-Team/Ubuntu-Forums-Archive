---
title: "Need an explaination"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by gilloz on 2007-12-18
I have been using Ubuntu 7.10 for about two weeks and it is functioning well.  In my searches for learning more about this OS, I came across something that I would like someone to set me straight.  I was looking at /etc/network/interfaces for networking setup and mine presently reads:

auto lo
iface lo inet loopback

The instructions on the Ubuntu forums say it should read:

auto eth0
iface eth0 inet loopback

Since I haven't had any problems with my Internet connection, should I have to make this change or just leave it alone?

---

### Post by chris4585 on 2007-12-18
if it works i wouldnt bother with it in my opinion, but i'm not a guru

---

### Post by mellowd on 2007-12-18
It's putting a virtual loopback interface on your pc's loopback as opposed to its ethernet card. If it works though leave it as be.

---

