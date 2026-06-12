---
title: "system monitor bugg"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by geek-at-heart on 2010-12-21
This is my fourth Ubuntu 10.10 install. I stuck it on a IBM think center pentium 4  3 GHZ.  Everything is working great I looked at system monitor and it reads 2 CPU's!!!  CPU1 and CPU2, both functioning between 1 and 17% (each one varies not showing the same) I click on system and under hardware it reads: processor0; Intel(R) Pentium(R) 4 cpu 3GHz; and processor1; Intel(R) pentium(R) 4 cpu 3GHz.Like I said, everything is working great but this is really wierd. I've had the case open and I'm sure there is only one cpu there. Will this cause any problems? Or is there a way to fix this? The past 3 machines I stuck ubuntu on never had this problem. Thanks for your input.

---

### Post by 3rdalbum on 2010-12-22
Many Pentium 4 CPUs have a feature called "Hyperthreading", which presents two CPU cores to the operating system. The CPU only really has one core, but when one thread of execution is blocked and waiting for data, the CPU can switch to the second thread (the virtual core) to get some work done in the meantime.

In short: This is not a bug, this is a feature of your computer's CPU.

---

### Post by geek-at-heart on 2010-12-22
Wow! this old P4 is sounding pretty cool right now. Thanks for the info . Problem solved!!!!!!!!!

---

