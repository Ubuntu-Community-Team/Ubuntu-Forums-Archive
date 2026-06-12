---
title: "SMC2862-W Memory leak"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by mhueting on 2007-04-19
Hi,

I have finally been able to install my SMC2862-W EZConnect USB wireless receiver. But if I fire it up with

```
ifup rausb0
```

the computer slows down like HELL. Mouse-movement is completely stuttery, and I am completely unable to use the machine.

This must be because of some memory leak, but how do I track this down?

I've looked on the internet, and I've found a site that mentions this memory leak, but the person that was dealing with it said "he would hunt it down later". He never did. So I'm reallllllly looking forward to any kind of solution to this very annoying problem :guitar:

---

### Post by mhueting on 2007-04-20
Anyone? I'm a noob, so I could use some help :mrgreen:

---

### Post by mhueting on 2007-04-20
update:

If I use the "top" command, I can see that when the device is plugged in, ifconfig uses up about 95% of my cpu power.

All I can say: :confused: :confused: :confused:

---

