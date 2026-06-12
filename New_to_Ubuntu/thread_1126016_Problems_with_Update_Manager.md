---
title: "Problems with Update Manager"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by rideburton56 on 2009-04-15
Is anyone else having trouble with update manager and the acroread package?  The system tells me it can do a partial upgrade, which would involve removing the packages acroread-plugins and mozilla-acroread,installing ash, and upgrading acroread.  Whats the deal?  I'm running 8.10 studio edition.

---

### Post by cariboo on 2009-04-16
Usually when you're asked if you want to do a partial upgrade, it means some of the dependencies are missing. I would wait a couple of days and try again. If you absolutely need the updated program, you can open a terinal and type:

```
sudo aptitude safe-upgrade
```

Doing a partial upgrade is not recommended.

Jim

---

