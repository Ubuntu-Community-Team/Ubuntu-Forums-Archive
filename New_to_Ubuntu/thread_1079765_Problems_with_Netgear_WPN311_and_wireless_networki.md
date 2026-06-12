---
title: "Problems with Netgear WPN311 and wireless networking."
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Colonel Forbin on 2009-02-24
I am at my wits end here. I've looked all over community documentation, the forums, madwifi, and others. I have a netgear WPN311 and I can not get it to work. Can someone please post a walk through of how to get it going. Please

---

### Post by swoll1980 on 2009-02-25
> **Colonel Forbin said:**
> I am at my wits end here. I've looked all over community documentation, the forums, madwifi, and others. I have a netgear WPN311 and I can not get it to work. Can someone please post a walk through of how to get it going. Please

try installing restricted modules maybe
```
sudo apt-get install linux-restricted-modules-`uname -r`
```
that should install the driver you need for that card

---

### Post by Colonel Forbin on 2009-02-25
> **swoll1980 said:**
> try installing restricted modules maybe
```
sudo apt-get install linux-restricted-modules-`uname -r`
```
that should install the driver you need for that card

That didn't work. It just said could not find package linux-restricted-modules-uname -r

---

