---
title: "How to? config NTOP with wireless wlan0?"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-07-21
I have installed ntop and cannot see stats at localhost:3000 - that page shows the interface looking at eth0 and I have wlan0.

I tried following a how-to for Ubuntu & ntop, but the app must have changed because /etc/init.d/ntop has NO place which lists eth0 and I cannot change that.

Anybody got a clue?

---

### Post by Mark_in_Hollywood on 2011-08-01
I have found a solution. Please see the post labeled 

Configure NTOP for Wireless

---

### Post by viesur on 2012-12-09
try ntop --interface wlan0

---

