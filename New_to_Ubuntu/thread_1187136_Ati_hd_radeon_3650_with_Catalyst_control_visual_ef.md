---
title: "Ati hd radeon 3650 with Catalyst control visual effect lag"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by csl5010 on 2009-06-14
I am experiencing 1 -2 second lag when resizing windows or minimizing/maximizing windows in ubuntu.
When no visual effect, the resizing works with no delay/lag.
But with normal/extra visual effect, everything has a 1-2s delay.

I have ATI HD radeon 3650 with ATI Catalyst installed already. Any advice how to kill the delay?

Thanks.;)

---

### Post by wpshooter on 2009-06-14
> **csl5010 said:**
> I am experiencing 1 -2 second lag when resizing windows or minimizing/maximizing windows in ubuntu.
When no visual effect, the resizing works with no delay/lag.
But with normal/extra visual effect, everything has a 1-2s delay.

I have ATI HD radeon 3650 with ATI Catalyst installed already. Any advice how to kill the delay?

Thanks.;)

1) Do not use visual effects.
2) Find a more compatible driver for your video card.
3) Get an Invidia video card.

---

### Post by csl5010 on 2009-06-14
> **wpshooter said:**
> 1) Do not use visual effects.
2) Find a more compatible driver for your video card.
3) Get an Invidia video card.


Thanks.
I found answer 4) add this line to about:config in firefox -"config.trim_on_minimize" =True. This helps minimize the delay.

---

