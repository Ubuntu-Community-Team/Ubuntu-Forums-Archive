---
title: "CPU throttled unnecessarily"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by jstateson on 2010-02-06
I have an AMD dual opteron system with Cool and Quiet (also called PowerNow) enabled in the bios.  This system is dedicated to running BOINC and all 4 cores are 98%+ busy all the time.

Unaccountably, this system, Tyan S2895, is being throttled from the normal 2.6ghz down to 1ghz.  The system boots at 2.6ghz as shown in the bios post, but as soon as ubuntu 8.04 starts, the cpu speed drops to 1ghz.

I disabled PowerNow to fix the problem and the cpu is running at a constant 2.6ghz.

This should not have happened.  BOINC supposidly is keeping all cpu's running at %100 full load so the PowerNow should not have been activated.

I assume this is a ubuntu bug although it could possibly be BOINC related.

Solved [HERE]("http://aqua.dwavesys.com/forum_thread.php?id=446") although with %100 utilization one would think that throttleing the CPU would be a bug and not a feature.

---

