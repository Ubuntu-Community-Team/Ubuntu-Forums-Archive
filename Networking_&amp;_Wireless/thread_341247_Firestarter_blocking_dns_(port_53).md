---
title: "Firestarter blocking dns (port 53)"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by QOLIM on 2007-01-18
Every time I boot my pc I have to allow  port 53 (dns) to the inbound policy in firestarter,
cus otherwise firestarter blocks it..

I already have like 10 times "allow dns port 53" in my allow inbound list
and every time I start up ubuntu I have to add it

Anyone knows a solution to this?

Thx,

QOLIM

---

### Post by glahhg on 2007-01-19
Something similar happens to me, and I don't even have Firestarter installed.  (I used to have it installed).  Every time I reboot the machine I can't connect to myself on port 5901 (for vnc over ssh), and I have to install then uninstall Firestarter to get it to work.  Did Firestarter modify a startup file somewhere that messes with iptables to block everything?  
Help is appreciated!

---

### Post by QOLIM on 2007-01-21
Got it fixed now,
I cleande up the policy list and found out there was a "allow dns for lan-users" in it which prolly caused a confilct

---

