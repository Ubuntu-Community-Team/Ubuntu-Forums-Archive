---
title: "problem with Java"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by wog on 2011-02-22
I'm trying to play minecraft. The webpage ([http://www.minecraft.net/](http://www.minecraft.net/)) claims it specifically wants Sun Java. 

The command ```
java -version
``` claims I have:
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.5) (6b20-1.9.5-0ubuntu1)
OpenJDK Server VM (build 19.0-b09, mixed mode)

I go into Ubuntu Software Center and remove OpenJDK and it says it does it. Then I install sun-java6-bin and sun-java6-plugin, and when that's done, I close Ubuntu Software Center and then check version again. And it always reads the same as before I supposedly uninstalled OpenJDK.

Can someone help me figure this out, please?

---

### Post by gandaran on 2011-02-22
open synaptic package manager and check that the icedtea-plugin is completely removed from the system only the sun-java6-plugin is installed, you may keep the rest of openjdk-java packages installed if you wish.

---

### Post by wog on 2011-02-22
Thank you so much! That worked like a charm. :)

---

