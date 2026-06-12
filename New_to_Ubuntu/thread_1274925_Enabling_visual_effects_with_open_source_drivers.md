---
title: "Enabling visual effects with open source drivers"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-25
Hi,

I was using the fglrx driver but the open source drivers play so much nicer with my dual monitor setup.... I was wondering whether you could enable "normal" visual effects using the radeon driver?

The main reason is just to get rid of that ugly black box that appears when you minimize windows... i'm not so fussed on visual effects anyway.

Cheers

---

### Post by 3rdalbum on 2009-09-25
> **humphreybc said:**
> Hi,

I was using the fglrx driver but the open source drivers play so much nicer with my dual monitor setup.... I was wondering whether you could enable "normal" visual effects using the radeon driver?

There's an easy way to find out!

Some ATI graphics chips can run Compiz on the ordinary "ati" or "radeonhd" open-source driver; I don't know if yours is one of them, but you can certainly try it:

```
compiz --replace
```

---

### Post by humphreybc on 2009-09-25
Okay, I did that... then tried to enable normal effects, and it still says "desktop effects could not be enabled"

- does this mean my card isn't one of them?

---

