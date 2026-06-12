---
title: "Partitions &amp; mount points size distribution ??"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Nico-dk on 2008-12-08
So thanks to you helpful people, I've decided to go dual boot (XP / Hardy Heron).

Next question is, what would be a good way to split up a 160gb hdd, when XP will be used for gaming only?

My thoughts:

25gb - XP + win apps and win swap
10gb - 8.04LTS + /Boot, /Usr (/dev??)
4gb - /Swap
25Gb - /Home
40Gb - Win Games
10Gb - Audio/Music (shared by Xp+HH)
20Gb - Graphics (shared by Xp+HH)
26Gb - (undecided)

Follow-up question:
Does it matter where I place what partion or mount point?
I know /Root must be first, but can /swap and /Home be placed in whatever order i choose?

Feedback more than welcome, and greatly appreciated :)

---

### Post by ugm6hr on 2008-12-08
Seems fine.

Although 4GB swap is a lot; 700MB is plenty for most people, unless you use suspend to RAM.

XP must be on a primary partition.  Everything else can be wherever you want.  Some people suggest the fastest part to read is the end of the HD, (centre of disk), so swap is perhaps best there.

---

### Post by Nico-dk on 2008-12-08
I've got 4gb Ram, so I figured a nice 4gb for swap would fit in well ... But i guess that's only needed for wins

---

### Post by Captain_tux on 2008-12-08
I have 2GB RAM and 2GB swap on my laptop with 8.04... suspend to RAM works well.

---

### Post by carml on 2008-12-08
On Linux I have "only" 266,67 MB reserved for swap,with 2 GB of RAM,and don't notice problems.
In my humble opinion you can reserve a minimum space for swap,choose you the dimension and try any options if you want,then reserve the rest for data and for the systems ):P.

---

