---
title: "Synaptic error message"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by old_dope on 2009-03-03
Could someone please tell me what this means please

---

### Post by taurus on 2009-03-03
> **old_dope said:**
> Could someone please tell me what this means please

Can you include the whole error message?

---

### Post by old_dope on 2009-03-03
Sorry about forgetting to put up the error message. So here it is:

E: dpkg was interrupted, you must mannually run 'dpkg -configure -a' to correct the problem. E:_cache->open() failed, please report.

Thanks for the help

---

### Post by konqueror7 on 2009-03-03
just type in the terminal,
```
sudo dpkg -configure -a
```

---

### Post by taurus on 2009-03-03
Close synaptic.  Then, open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

