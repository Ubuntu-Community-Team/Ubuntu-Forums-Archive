---
title: "[SOLVED] iptables and Firestarter"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by Megatog615 on 2007-09-02
I've recently installed Firestarter, configured it, and realized I don't need it for my setup. How do I completely remove it, then restore iptables to the way it came with Ubuntu?

---

### Post by moore.bryan on 2007-09-02
[I]```
sudo aptitude remove --purge firestarter
``` for the wall and
```
sudo iptables --flush
``` for the tables.
[/I]

---

### Post by Megatog615 on 2007-09-02
I think that may have inadvertently blocked all connections. I'm on my laptop now. I'll reboot to see if that fixes it.

Yup! That fixed it. Thanks!

---

### Post by moore.bryan on 2007-09-02
[I]no problem.  happy ubuntu-ing.

oh, and you may want to click on "thread tools" in the top right and mark this as "solved."

keeps things clean around here...
;-)
[/I]

---

