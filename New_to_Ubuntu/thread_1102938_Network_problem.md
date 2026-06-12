---
title: "Network problem ?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by alket on 2009-03-22
Im connected throw one rooter with 2 Pcs, one is Windows other is Ubuntu, When I connect to windows its automatically connects to internet without IPs or Mac Address but in Ubuntu it doesnt work,

Rooter has ADSL Connection, but it comes with LAN connection to my Ubuntu.

---

### Post by halitech on 2009-03-22
what type of connection between the router and the computer?

What version of Ubuntu?

can you post the output of
```
lshw -C network
``` and```
sudo ifconfig
```

---

### Post by alket on 2009-03-22
between router and computer is a lan conection.

The last version of ubuntu.

The output is:
Network0 disabled
Network1 disabled

---

### Post by alket on 2009-03-22
How can I enable Network:0 and Network:1

---

### Post by halitech on 2009-03-22
wired or wireless connection?

what was the output of lshw -C network?

---

