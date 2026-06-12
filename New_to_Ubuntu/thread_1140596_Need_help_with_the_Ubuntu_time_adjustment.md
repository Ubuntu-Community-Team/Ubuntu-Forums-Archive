---
title: "Need help with the Ubuntu time adjustment"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by cheese123 on 2009-04-27
Everything I boot Ubuntu the time is an hour ahead of what its suppose to be. Any ideas on what the problem could be? I'm using Ubuntu 9.04, dual booting with XP.

---

### Post by lisati on 2009-04-27
Could be a time-zone issue, or just that the clock's out. You should be able to check the time-zone settings on the System->Administration->Time and Date menu item.

---

### Post by cheese123 on 2009-04-27
> **lisati said:**
> Could be a time-zone issue, or just that the clock's out. You should be able to check the time-zone settings on the System->Administration->Time and Date menu item.

That may have done it, thanks! :)

---

### Post by llamabr on 2009-04-27
Once you have your time zone set correctly, you can also run ntpdate.  I use a server at GA Tech:

```
nptdate rolex.peachnet.edu
```

The command to set your time zone is TZ:

```
#TZ='America/New_York'
#export TZ

```

---

