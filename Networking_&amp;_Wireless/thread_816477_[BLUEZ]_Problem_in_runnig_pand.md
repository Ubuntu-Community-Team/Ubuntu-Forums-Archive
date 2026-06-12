---
title: "[BLUEZ] Problem in runnig pand"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by pernacentus on 2008-06-02
Hi everybody, I got a problem i can't solve. When i try to set up a PAN network with bluez everything goes fine. Now i have to destroy this network and build another one, where a node PANU of the old network is going to be the NAP of the new one. When i type ```
pand --master --role NAP -sdp --listen
```
nothing seems to happen, in fact if i type ```
ps auwx | grep pand
```
it returns only ```
1000     31882  0.0  0.0   3004   768 pts/0    S+   12:06   0:00 grep pand
```
which means that the daemon was not started. Sorry for my awful english, i hope you could understand and give me some help.

---

