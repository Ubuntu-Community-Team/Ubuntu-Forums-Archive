---
title: "Bip Sound as I type"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by rafaelgranado on 2010-12-14
I've just installed Ubuntu 10.10 on my DELL Vostro 3500.
I've configured the hardware and themes to my own preferences, but something still bugging me.
As I type this thread, my keyboard is beeping.

Anyone knows why this thing may be happening?

I am an experienced IT PRO and heavy Windows User.

---

### Post by SpockVulcan on 2010-12-14
Try adding this line at the end of your /etc/modprobe.d/blacklist

```
blacklist pcspkr
```

---

### Post by rafaelgranado on 2010-12-14
This entry is already there

---

### Post by pricetech on 2010-12-14
Check your BIOS.  Seems I remember a setting there for keyboard beeps.

---

### Post by rafaelgranado on 2010-12-14
That's it.

Sorry for my dumbness.

---

