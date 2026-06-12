---
title: "Netbeans Broken under Karmic"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by occams_beard on 2009-11-02
I really am at a loss. Over the weekend I upgraded to Ubuntu 9.10 and now when I start Netbeans my processor spikes to 100% and "Task Scanning" just never stops and Netbeans becomes slow and unusable.

I eventually just have to kill it. Strangely, after restarting it again it'll work properly. Although, if I then open a project... BAM, it's back to Task Scanning for infinity.

I've tried deleting all .nb* and .netbeans* directories in my home dir and I've also tried reinstalling Netbeans, but it's the same thing.

I really don't know what could have changed in Ubuntu to cause this. I'm using the same version of Java as I had in 9.04 (1.6.0_16 sun java).

I'm also launching netbeans with:
--laf Metal -J-Xms64m -J-Xmx786m -J-XX:PermSize=64m -J-XX:MaxPermSize=300m

Any ideas? Anyone else experiencing this under Ubuntu?

---

