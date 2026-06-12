---
title: "openoffice.org wont update due to error"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by libihero on 2009-08-31
for some reason my openoffice wont update at all.  i added it to the sources but it keeps on giving me an error.  i added pics for more details.  thanks!

---

### Post by sydbat on 2009-08-31
Go into Synaptic (System > Administration > Synaptic) and click Custom Filters (lower left). It will give you a few options in the left pane...one of which should be Upgradable. Click on it and your OOo should be listed there.

I have found this is the best method to upgrade Open Office, as Update Manager can mess things up when it says "Partial Upgrade".

---

### Post by colau on 2009-08-31
Report.
```

sudo dpkg --configure -a
sudo aptitude update
sudo aptitude install openoffice.org

```

---

### Post by Hagar Delest on 2009-09-02
Or try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

