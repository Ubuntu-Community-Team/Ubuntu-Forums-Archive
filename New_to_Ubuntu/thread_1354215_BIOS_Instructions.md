---
title: "BIOS Instructions"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by nnjond on 2009-12-13
Hi,

My Master IDE 0 has is my hdd and my dvd is allso Master on IDE 1 but i think it should be  a slave to avoid conflicts but i cant figure out how i do it. Should i worry?

---

### Post by Cheesemill on 2009-12-13
They're not conflicting, one is on channel 0 and the other is on channel 1, these are completely separate. If you had two drives both set to master on the same channel then the system wouldn't even boot.

If you did want to change the master/slave configuration then you need to open up the machine and either swap the cables around or change the jumpers on the drives.

The way you are currently set up is the best configuration.

---

