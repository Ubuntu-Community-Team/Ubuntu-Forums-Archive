---
title: "Suspend/hibernate doesn't work, even though log says success"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Djalmahal on 2010-05-03
HI,

my Asus G60JX fails to suspend and hibernate, a look at the log files comes up only with succes (log file as attachment).

Can anybody give me some feedback, enabling suspend at least would be great.

Specs
i5 processor
nvidia 360m
4gb ram
plenty of swap (5GB)

---

### Post by madjr on 2010-05-04
hm

could be the video drivers

are the open source drivers working with suspend?

is the express gate (fast boot linux) also suspending successfully?

after you checked those try opening a bug report on launchpad, am sure there should be a fix, specially if older versions of ubuntu were working well

---

### Post by tristan.cole on 2010-05-04
From what i have heard from other people, the Suspend/hibernate is broken for many computers. it doesnt seem to be computer or even version specific(ie netbook, desktop)

---

### Post by Djalmahal on 2010-05-05
I didn't work on Karic, i was hoping it would work with Lucid. Before installing the proprietary NVidia drivers I tried suspend with the Noveau drivers, then didn't work as well, so seems to me it is not the Nvidia driver.

I never tried Express Gate, shall have a look at it.

Andreas

---

