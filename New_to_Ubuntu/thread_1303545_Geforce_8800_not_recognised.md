---
title: "Geforce 8800 not recognised"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by .James on 2009-10-28
I am very, very confused. Just getting started with Ubuntu - ran the LiveCD a couple of times and played around installing drivers for my graphics card - all fine. However, now I've installed it to my HDD ("it" being 9.04), the GPU isn't listed in the Hardware Drivers section.

I've googled to find similar problems - but my main issue is that I can't see any logical reason why this would be the case. The card works (the display is plugged into it), I just want to install the correct drivers for it. Can anyone help?

---

### Post by wojox on 2009-10-28
Try this thread: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

---

### Post by philinux on 2009-10-28
> **.James said:**
> I am very, very confused. Just getting started with Ubuntu - ran the LiveCD a couple of times and played around installing drivers for my graphics card - all fine. However, now I've installed it to my HDD ("it" being 9.04), the GPU isn't listed in the Hardware Drivers section.

I've googled to find similar problems - but my main issue is that I can't see any logical reason why this would be the case. The card works (the display is plugged into it), I just want to install the correct drivers for it. Can anyone help?

Probably because the system needs to be updated first,

Open a terminal
```
sudo apt-get update && sudo apt-get upgrade
```

Then try sys>admin>hardware drivers.

---

### Post by ukripper on 2009-10-28
I'd agree with philinux to update the system first and go from there!

---

### Post by .James on 2009-10-28
Thankyou very much - will try that later.

---

