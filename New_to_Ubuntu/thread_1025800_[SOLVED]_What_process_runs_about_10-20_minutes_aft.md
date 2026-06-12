---
title: "[SOLVED] What process runs about 10-20 minutes after startup?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by thadacto on 2008-12-30
This morning I was using my open Org word processor when I noticed that some program was taking over most of my processor (Dual core). The red light on the tower was almost permanently on but flickering a little. I opened System Monitor, and went to  processes but there was nothing marked as "Running"; everything was sleeping. I have noticed this before, but this time it continued for about 4-5 minutes.
I feel something was checking my computer but I don't know what nor why.
Any input would be much appreciated.

---

### Post by Shazaam on 2008-12-30
It might have been Tracker or the auto-updater.
To find out what is running open terminal and enter...
```
top
```
That shoud give you more info. You might also want to try htop. It's in the repos.

---

### Post by taurus on 2008-12-30
It's probably the updatedb.

---

