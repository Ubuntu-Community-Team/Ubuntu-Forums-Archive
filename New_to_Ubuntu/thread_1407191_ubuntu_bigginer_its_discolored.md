---
title: "ubuntu bigginer its discolored"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by deathbydoubleG on 2010-02-15
i just installed ubuntu and it is very discolored (e.g. the letteres i'm typing are greenish and a picture that would normaly be blue is green and orange
it is a RV770 [Radeon HD 4850] graphic card

:popcorn::)thanks very much my problem is now solved thanks to jkenl46:popcorn::P

---

### Post by jken146 on 2010-02-15
First, check that the cable connecting your PC to your screen has not come loose (check both ends).

If it's not that, go to System->Administration->Hardware Drivers and see if there is a different driver to install. If there is, do that and reboot.

Failing that, tell us what graphics card you have. If you don't know, open a terminal and type ```
sudo lshw -c video
``` and post the output here.

---

