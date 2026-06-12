---
title: "htop displays duplicate tasks"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by zorblek on 2009-08-17
When I use htop, it shows multiple entries for some tasks. For instance, Firefox is listed several times with nearly identical entries (only the PIDs are different). Is there some way to make it only display a task once?

---

### Post by scorp123 on 2009-08-17
> **zorblek said:**
> When I use htop, it shows multiple entries for some tasks.  Maybe it's showing threads that have been spawned by the main process?

Try this: Launch "htop" and press F2 for setup. Then go into "Display Options" and activate these options:
[LIST]
[*][x] Tree view
[*][x] Display threads in a different color
[*][x] Highlight program "basename"
[*][x] Highlight megabytes in memory counters
[*][x] Leave margin around header
[/LIST]

Now those "double entries" should have different colors and they should be arranged in a tree-like fashion so you can see which process spawned which other process. Now it should be way easier to see which really is the main process and what other entries are just threads ("sub-processes") that got spawned.

I hope this helps to clear up the confusion a bit?

---

### Post by zorblek on 2009-08-17
That is helpful, thanks. While rooting around in the display settings, I also found "Hide userland threads" which I believe is what I was looking for. Thanks again!

---

