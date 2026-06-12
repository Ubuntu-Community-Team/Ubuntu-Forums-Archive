---
title: "bcm43xx strickes back [with Edgy Eft]"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by JackTheKnife on 2006-10-31
I did upgrade to Edgy Eft and I got after all that wireless doesn't work with ndiswrapper. When I try

```
sudo modprobe ndiswrapper
```

I got:

> FATAL:Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndsiwrapper/ndiswrapper.ko): Invalid argument

First I checked if everythings is ok with ndiswrapper -l.

Any idea? Thanks

---

### Post by JackTheKnife on 2006-10-31
Problem fixed! TIP: ndisvrapper 1.1-5 doesn't work with 6.10

---

