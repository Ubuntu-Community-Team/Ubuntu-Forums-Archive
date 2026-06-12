---
title: "Fuppes error"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by adobrakic on 2009-01-21
I get the following error when i try to do 'sudo fuppes':

```
[ERROR] failed to bind socket to : 192.168.10.102:5000
[exiting]

```

it happened to me before, and it fixed when i switched the port to 5000, but now it's happening again and I really don't want to keep switching the port every single time this happens.

---

### Post by nhasian on 2009-01-21
i'm not sure how to prevent that error from happening, but i was wondering if you'd tried ushare out?  I gave up on fuppes a long time ago and have been very happy with ushare ever since.

---

### Post by adobrakic on 2009-01-21
Looks good on google, thanks, I'll try it out.

---

### Post by infallible on 2009-01-31
I've only gotten that error when I try to run fuppes twice. It can't latch onto it's default port, because the port is taken by the first instance of fuppes. In your case, it may be another program taking the port, or a firewall blocking the ports use.

---

### Post by adobrakic on 2009-01-31
i just changed it to randomize the port

---

