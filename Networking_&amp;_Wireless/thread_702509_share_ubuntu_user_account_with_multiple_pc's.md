---
title: "share ubuntu user account with multiple pc's"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Peturrr on 2008-02-20
I am currently using a laptop and a desktop PC, both with Ubuntu 7.10.
I would love to be able to have the same settings, documents etc on both desktops. What is the right approach for this?

Should I just mount /home from a NFS share ?
If so, what about things like compiz settings? (my laptop doesn't support it, my desktop does and has it enabled)

Any other techniques or possibly nasty things that I should think about when deploying this?

---

### Post by Rogers on 2008-02-20
I just have the same user account on both machines and do a nightly rsync.  Sometimes the simplest solutions are the best.  You could also just setup VNC on your desktop and VNC to it.

---

