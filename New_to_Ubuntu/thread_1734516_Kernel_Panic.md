---
title: "Kernel Panic"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by skinnyj on 2011-04-20
I recently downloaded the recent kernel update for 10.10. I tried booting into it but instead of a splash screen or anything else coming up, this happens:
```
[  0.715068]  Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[  0.715102]  Pid: 1, comm: swapper Not tainted 2.6.35-28-generic #50-Ubuntu
```And there's a call trace log after that. After the end of the trace log, it is unresponsive to keyboard commands. Strangely, the 2.6.35-27-generic kernel works just fine. What's going on?

---

### Post by TeoBigusGeekus on 2011-04-20
These things happen from time to time.
Boot up with the older kernel and wait for a newer one.

---

