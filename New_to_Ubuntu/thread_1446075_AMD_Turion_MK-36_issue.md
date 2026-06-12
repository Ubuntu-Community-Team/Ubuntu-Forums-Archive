---
title: "AMD Turion MK-36 issue?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Kaperww on 2010-04-03
Hi there.

I've installed Ubuntu 9.10 on my Acer 5050 laptop. The laptop works pretty well, but when I type cat /proc/cpuinfo in terminal, then the CPU shows as it only is 800mhz. Even though I know it have 2000mhz.
Does this matter?

Sorry about my English, I'm still learning.

Cheers,

Kasper

---

### Post by NightwishFan on 2010-04-05
I am willing to bet you just have CPU frequency scaling available (Which is a good thing). A simple way to check is to add the cpu frequency scaling monitor to the gnome panel. If it seems to be running at 50% power, then you just have power saving enabled.

This is no problem. Linux will automatically scale to use a higher frequency when needed. Leave the default settings enabled. When you machine is idle it will run with less noise and power, with no loss to performance.

---

