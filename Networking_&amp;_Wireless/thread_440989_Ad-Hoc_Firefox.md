---
title: "Ad-Hoc Firefox"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by Psicolonia on 2007-05-12
Hi everyone im connected to an ad-hoc natwork and my static ip is 120.0.0.2
my internet connection is behing a proxy at 120.0.0.9

when i ping 120.0.0.9 nothing happens

when i ping -I eth1 120.0.0.9 everything is fine

proxy is running great i can access it on windows.

however, even when i'm connected and i ping my wireless friend, firefox refuses to access eth1.

basically my configuration is just like on windows, only on windows firefox gets net.

on linux it does not! :( can someone help?

i've tried: sudo ifdown eth0

didn't work...

---

### Post by spd106 on 2007-05-13
Have you added the proxy details to Firefox?

---

### Post by Psicolonia on 2007-05-13
oh yes, i use switch proxy add-on and everything. but i did double check it... so that's not it...

---

### Post by spd106 on 2007-05-13
Have you checked the routing table?

---

### Post by Psicolonia on 2007-05-13
hummm... it's on... don't know why, i run a hundred commands try to fix vnc... so... maybe it was one of them... Thanks anyway spd106 ;)

---

