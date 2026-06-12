---
title: "NIC help"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by DivisionMatrix on 2009-08-22
Hi All,   My onboard nic died for no apparent reason, fortunately I had an old one in the closet that I plugged in, it works perfectly in ubuntu, but windows can't even tell me what kind of card it is so I can get the right drivers (the card is like 6 years old, I have no documentation or anything for it) how can I find out the actual model number of the nic? 
I know it's a netgear card, but thats all I can find...
Thanks!

---

### Post by sandyd on 2009-08-22
in ubuntu, open up a terminal and type in
```

lspci

```
thats one of the benifits of suing ubuntu. always. it has most drivers by default except for the ones that are newer such as creative X-Fi or some other wifi drivers.

---

### Post by DivisionMatrix on 2009-08-22
Thanks bunches, turns out that card is so old vista doesn't support it at all. Thank god for linux, at least I have internet till I can get a new card...

---

