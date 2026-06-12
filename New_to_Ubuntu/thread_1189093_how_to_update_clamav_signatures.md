---
title: "how to update clamav signatures?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by Rigorous on 2009-06-16
Hello,

I am trying to update my  clamav signatures but it says i must be root to install updates, how do i do so?

---

### Post by arochester on 2009-06-16
Assuming you have installed clamtk (the graphical front-end of clamav) start it from the Terminal with the command: > sudo clamtk

---

### Post by MrWES on 2009-06-16
> **Rigorous said:**
> Hello,

I am trying to update my  clamav signatures but it says i must be root to install updates, how do i do so?

```
sudo freshclam
``` from the terminal.

However, freshclam -d should be running. To check, type this at the terminal:

```
ps aux | grep freshclam
```
By default, if freshclam is running, it updates 24 times a day.

Bill

---

