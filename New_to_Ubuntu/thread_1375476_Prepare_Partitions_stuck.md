---
title: "Prepare Partitions stuck"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Mitch Cichocki on 2010-01-07
Installing 9.10. I get to Step 4 of 7, Prepare Partitions screen, and it's just stuck. There's nothing to do. All the options are blanked, no drop down menus, nothing. I can cancel the install or go back. What gives?

---

### Post by stoogiebuncho on 2010-01-08
Did you check the disc to make sure there weren't any errors in the burn?  It's one of the options when you first boot the disc.

If that's the problem, try burning again at the slowest speed possible.

---

### Post by oldfred on 2010-01-08
Do you already have 4 partitions? Ubuntu cannot create more if all 4 are set up and are primary partitions.

From liveCD.

sudo fdisk -l  (el not 1 or I)

---

