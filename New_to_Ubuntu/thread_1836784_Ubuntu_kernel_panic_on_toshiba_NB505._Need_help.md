---
title: "Ubuntu kernel panic on toshiba NB505. Need help"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by Ben6969 on 2011-08-31
Hello everybody! I just installed ubuntu 11.04 using wubi. When I boot into it, its on the intro screen that shows all the apps installed or something. Then, all of a sudden it go to a black screen that says call trace with numbers. It also says kernel panicked. After that I booted into windows. What do I do to fix this problem? Specs: 250 GB hard drive, 1 GB RAM, intel atom processor. Toshiba mini NB505

---

### Post by Rubi1200 on 2011-09-01
Hi and welcome to the forums :-)

Please start by posting the make/model of computer and the full specifications.

Thanks.

---

### Post by Ben6969 on 2011-09-04
It's got 250 GB hard drive, 1 GB RAM, intel atom processor

---

### Post by Rubi1200 on 2011-09-05
Kernel panics and trace numbers may indicate an issue with RAM or possibly have some other cause.

I suggest you look in the logs and see if there is something that may give us a clue as to what is happening.

The relevant logs are dmesg, syslog, and kern.log; they can be viewed with the Log File Viewer available via System Administration.

---

