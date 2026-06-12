---
title: "Custom Apache 2 configuration file scheme"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by sheldonnbbaker on 2009-10-04
Hi everyone,

Is is possible/recommended to have just one (or a few) configuration files in apache (e.g., just apache2.conf) instead of symlinking between *-available and *-enabled and all that?

I think I would like it better that way, but if it's not recommended, I guess I'd stick with the current way.

Thanks

---

### Post by crolanx on 2009-10-04
Of course is it possible, but not really wise at all.

The idea behind the folders *-available and *-enabled is that you easily can activate and deactivate virtual hosts and the modules which apache is supposed to load.

For other configuration you can use configuration files without putting them in *-available, but you also may use those folders.

---

