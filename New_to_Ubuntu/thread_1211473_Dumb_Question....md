---
title: "Dumb Question..."
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Autumnie88 on 2009-07-12
I have forgotten where to go to enter the run codes.  Can anyone help me out?

---

### Post by LewRockwell on 2009-07-12
> **Autumnie88 said:**
> I have forgotten where to go to enter the run codes.  Can anyone help me out?

Command Line Interface perhaps?

Terminal?

.

---

### Post by AndThenWhat on 2009-07-12
Press ALT + F2 or (Applications -> Accessories -> Terminal).

Not sure if that is what you meant.

---

### Post by Autumnie88 on 2009-07-12
That is what I needed to know.  Thanks.  Unfortunately, the update installer told me that I needed to run dpkg --configure -a.  I did that, and it gave me this 

[B]dpkg: error processing update-notifier (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 update-notifier

Any ideas on how to fix this so I can install the updates?

---

### Post by egalvan on 2009-07-12
> **Autumnie88 said:**
> update installer told meI needed to run
 dpkg --configure -a.

  I did that, and it gave me this 

[B]dpkg: error processing update-notifier (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 update-notifier

Any ideas on how to fix this so I can install the updates?


The proper way is to run it as root...
```
**sudo** dpkg --configure -a
```

Else, you have deeper problems than I can help with at this time.

---

