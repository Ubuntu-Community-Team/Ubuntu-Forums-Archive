---
title: "How to control CPU speed in 9.10 x64"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-02-23
I have an Asus 1005PE with a Atom n450. The n450 usually runs hot and at 1.67 ghz. I was wondering if there is a way to bring the CPU speed down to 1.0 ghz. And im talking about not through the CPU monitor

---

### Post by 3rdalbum on 2010-02-23
The Atom will speed-scale down to 800Mhz when it is not under load. This happens automatically and by default.

If it's constantly running at 1.67 GHz, then you might have a buggy program running that is continually running your CPU at 100%. Check System Monitor to see what it is, and then kill it.

---

