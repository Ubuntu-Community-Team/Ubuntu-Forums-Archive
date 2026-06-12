---
title: "wireless - a guide for when it doesn't work for newbies?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by dave148 on 2009-12-27
Hi all, I recently had to do a fresh install of ubuntu 9.10, and now my wireless buffalo usb card) isn't working. It worked fine in 9.04, I know it's supported somewhere in ubuntu, but how do I make it work? There's all sorts of threads about wireless not working in ubuntu, but none seem clear to me on what to do. 

Thanks.

---

### Post by coffeecat on 2009-12-27
> **dave148 said:**
> There's all sorts of threads about wireless not working in ubuntu, but none seem clear to me on what to do. 


There are all sorts of different wireless chipsets, and you need to know the chipset to know the solution. The make and model of the device doesn't help much. Manufacturers use different chipsets at different times but often keep the same model number.

So - open a terminal (Applications > Accessories) with the Buffalo USB plugged in and post the output of:

```
lsusb
```

That'll give us some information.

---

