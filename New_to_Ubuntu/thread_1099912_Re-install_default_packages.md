---
title: "Re-install default packages"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by DirectDebit on 2009-03-18
Does anyone know how to do a complete re-install of all default packages at command line?

---

### Post by kaixi on 2009-03-18
Are you having any specific issues?

---

### Post by spcwingo on 2009-03-18
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by DirectDebit on 2009-03-18
I uninstalled too many packages and lost my entire desktop, so instead of looking in the logs and restoring each package one by one i rather do a full default package install and start again removing.

---

### Post by kansasnoob on 2009-03-18
> **spcwingo said:**
> ```
sudo apt-get install --reinstall ubuntu-desktop
```

+1! That should do it.

---

### Post by DirectDebit on 2009-03-18
thats great thanks, i saw it straight after the reply, you can now close this post.

---

