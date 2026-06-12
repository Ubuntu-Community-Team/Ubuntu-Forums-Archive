---
title: "Complete removal of mplayer"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-01-26
I installed mplayer sometime ago and it needed about 22mb now when I removed mplayer using autoremove did it only free up about 17mb so 5mb are still there, can they be removed?

---

### Post by bwang on 2009-01-26
Try:
```

sudo apt-get autoremove

```
to remove any unneeded packages. Why the worrying over just 5 mb, anyway?

---

### Post by Hospadar on 2009-01-26
also perhaps by purging
for example
sudo apt-get install mplayer
sudo apt-get remove --purge mplayer

Often when packages are removed they leave behind config files so if you reinstall them they will stay configured the way you left them.
purging will remove these files as well.

Also autoremove is nice.  if you install a package that has dependancies, then later remove said package, autoremove will remove the dependancies that got installed if they are no longer needed by anything.

---

### Post by mister_pink on 2009-01-26
It's possible that some dependencies haven't been removed because they're required by something else you installed after mplayer. For example, if mplayer depends on a, b, c and d, and you later installed something else that depends on c, then only a b and d will be removed with mplayer.

---

### Post by Vantrax on 2009-01-26
> **mister_pink said:**
> It's possible that some dependencies haven't been removed because they're required by something else you installed after mplayer. For example, if mplayer depends on a, b, c and d, and you later installed something else that depends on c, then only a b and d will be removed with mplayer.

This tends to the the common reason, especially for that size of remaining files. I would not worry about this unless you have limited space.

You can also check in synaptic to use the orphaned packages filter to see what else you can get rid of (if you prefer the GUI).

---

### Post by SpinningAround on 2009-01-26
Thanks for the answers, got a 5 GiB / partition so try to keep "waste" packages to a minimum

---

### Post by Nero147 on 2009-01-26
Also check to make sure that it removed the "/home/user/.mplayer" directory. a lot of things leave your prefs in your home even when you remove them.

---

