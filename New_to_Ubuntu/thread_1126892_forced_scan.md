---
title: "forced scan"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-04-15
i know that every 20 starts ubuntu does a forced scan just to make sure everything is fine.  But how can you make it scan sooner?

---

### Post by Monotoko on 2009-04-15
boot up from Live CD and run fsck from the terminal

---

### Post by lamalex on 2009-04-15
you can force an fsck on next boot by opening a terminal and issuing this command
```
sudo touch /forcefsck
```
then reboot.

---

