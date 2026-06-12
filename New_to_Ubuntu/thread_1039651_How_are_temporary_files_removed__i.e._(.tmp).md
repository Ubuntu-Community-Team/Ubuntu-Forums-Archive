---
title: "How are temporary files removed  i.e. (.tmp)"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by a.v.l on 2009-01-14
How are temporary (.tmp) files removed in Ubuntu please?

---

### Post by jbrown96 on 2009-01-14
According to [this page]("http://ubuntu-tutorials.com/2008/01/19/changing-the-tmp-cleanup-frequency/") the files are removed after each reboot. You can find instructions to change the frequency on their too. 

To manually remove them, and this might affect stability (not sure!), you can use ```
sudo rm -rf /tmp/*
``` which will remove everything in the directory, but use it with caution; there may be essential files in there.

---

### Post by a.v.l on 2009-01-14
Many thanks.





> **jbrown96 said:**
> According to [this page]("http://ubuntu-tutorials.com/2008/01/19/changing-the-tmp-cleanup-frequency/") the files are removed after each reboot. You can find instructions to change the frequency on their too. 

To manually remove them, and this might affect stability (not sure!), you can use ```
sudo rm -rf /tmp/*
``` which will remove everything in the directory, but use it with caution; there may be essential files in there.

---

