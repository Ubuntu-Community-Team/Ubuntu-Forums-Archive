---
title: "Apt cache"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by melrokz on 2009-01-25
When I uninstall packages, I'd like those packages only to be deleted from the APT cache. Only then can I make a APTonCD with only my installed packages. How may I do this?

---

### Post by neotasic1 on 2009-01-25
> **melrokz said:**
> When I uninstall packages, I'd like those packages only to be deleted from the APT cache. Only then can I make a APTonCD with only my installed packages. How may I do this?

In the terminal, type:-  man apt-get 

Read in particular the options purge, clean and autoremove.

---

