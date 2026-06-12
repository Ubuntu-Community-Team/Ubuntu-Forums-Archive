---
title: "How do I remove packages that another package installed?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by offbyone on 2010-04-18
If a package installs a bunch of other packages, how does one remove the packages the first package installed? (For example, package A installs packages B, C, and D. Removing package A only gets rid of package A, but not B, C, and D. How do I remove package B, C, and D if I don't know what they are?)

Thanks.

---

### Post by asmoore82 on 2010-04-18
```
sudo apt-get autoremove
```

-OR-

In the "Synaptic Package Manager," you can go to "Status" ->
"Installed(auto removable)" and mark them for removal.

---

### Post by warfacegod on 2010-04-19
Package A will install B C and D packages that it needs to run properly. This isn't true *all* of the time but for the most part, its best to leave B C and D alone.

Just reread your post. If you want B C and D gone because a is now gone, use Synaptic to find A (it will be listed under All whether or not its installed) and check its dependencies.

---

