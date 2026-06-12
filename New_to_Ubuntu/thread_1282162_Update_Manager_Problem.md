---
title: "Update Manager Problem"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by not_yet on 2009-10-04
using Jaunty

update icon shows on the toolbar

when I click it it says I should try a partial update

when I say Ok, it tries to do a distribution update, and crashes?

cheers

---

### Post by MelDJ on 2009-10-04
you dont have enough space it seems

---

### Post by not_yet on 2009-10-04
notyet@ibex:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            198838116  60457080 128280572  33% /
tmpfs                  1677812         0   1677812   0% /lib/init/rw
varrun                 1677812       332   1677480   1% /var/run
varlock                1677812         0   1677812   0% /var/lock
udev                   1677812       192   1677620   1% /dev
tmpfs                  1677812        88   1677724   1% /dev/shm
lrm                    1677812      2192   1675620   1% /lib/modules/2.6.28-15-generic/volatile

---

### Post by DougieFresh4U on 2009-10-04
I would never do partial updates.
Have tried terminal to see what it really wants to do?

---

### Post by nhasian on 2009-10-04
yes try from a terminal with:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by not_yet on 2009-10-04
thanks for the replies, have tried the terminal, still the same problem?

---

