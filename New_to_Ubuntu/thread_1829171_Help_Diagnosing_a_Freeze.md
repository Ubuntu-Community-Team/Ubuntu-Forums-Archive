---
title: "Help Diagnosing a Freeze"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by Hishighness on 2011-08-20
Hey all, I've got Ubuntu 10.10 and it seems to want to freeze on me a lot. It could just be a coincidence but it seems to happen when I'm using Nautilus.

Now I know no one can diagnose a problem with the limited info I've given, but I'm running on 20+ years of experience with Windows and about 1.5 years of limited experience with Ubuntu, so I'm not well versed on troubleshooting procedures. So I'm wondering if there is some sort of debugging mode or something I can turn on that will keep a constant log that I can reference after a freeze to help diagnosing it. Any other tips would also be appreciated.

Thanks for your time.

---

### Post by Muskegman on 2011-08-20
One thing i would try is open terminal and type in "top" without the quotes 

This might give you an idea what may be hogging your system resources, it will show cpu usage and what program or application may be causing the freeze.

---

### Post by kyletstrand on 2011-08-20
Approximately how long does it stay up until it freezes?  For my curiosity, are you connecting to the internet via wireless?

---

### Post by Hishighness on 2011-08-20
> **kyletstrand said:**
> Approximately how long does it stay up until it freezes?  For my curiosity, are you connecting to the internet via wireless?
Well I just tried it and it was almost instant, say about 10 seconds.

This time it's a bit different, I can move my mouse around but nothing responds. Before the mouse cursor was frozen as well.

And yes, I am using wireless.

---

### Post by Hishighness on 2011-08-21
Seemed to be a problem with Samba. I uninstalled it and the freezing stopped. Now I've just got to figure out if I can reinstall it and fix it.

---

