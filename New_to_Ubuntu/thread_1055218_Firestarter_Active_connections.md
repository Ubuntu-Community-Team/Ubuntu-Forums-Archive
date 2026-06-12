---
title: "Firestarter Active connections"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by sp176 on 2009-01-30
I realize that firestarter is only a GUI to my firewall, but I am wondering if someone can help me figure out how many active connections a typical user should have.  I first turned this on after about 2 months of learning ubuntu, and installing various software, so this is not my basic ubuntu package.

Anyways, when I first turned firestarter on I found approx. 20 active ports, but with no data being transferred.  Should I be closing some of these?  What is normal on an idle computer? for internet browsing? or for p2p file sharing?

---

### Post by bodhi.zazen on 2009-01-30
It depends on what you are using your computer for.

You can get additional information on your traffic with several commands, I like :

```
sudo lsof -i -n -P
```

---

