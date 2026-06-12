---
title: "No free space, at all."
date: 2009-07-04
forum: New to Ubuntu
---

### Post by bmtlol on 2009-07-04
I cannot download/install anything. I have absolutley no space what-so-ever.


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G  472K 100% /
tmpfs                 439M     0  439M   0% /lib/init/rw
varrun                439M  104K  438M   1% /var/run
varlock               439M     0  439M   0% /var/lock
udev                  439M  164K  438M   1% /dev
tmpfs                 439M  244K  438M   1% /dev/shm
lrm                   439M  2.4M  436M   1% /lib/modules/2.6.28-11-generic/volatile

---

### Post by austinpsycho on 2009-07-04
Do you have a question?

---

### Post by nhasian on 2009-07-04
to free up some space try System->Administrator->Computer Janitor.

or from a terminal:

```
sudo apt-get clean && sudo apt-get autoclean
```

---

