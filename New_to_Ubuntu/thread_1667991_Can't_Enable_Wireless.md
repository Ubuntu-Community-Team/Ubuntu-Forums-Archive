---
title: "Can't Enable Wireless"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by PaulHA2 on 2011-01-15
I have a brand-m=new Dell N5010 Inspiron. Ran 10.04 for a week under WUBI, liked it, decided to commit. Now, even with the driver updated and working, after a clean full install, it won't let me enable the wireless. what to do?

---

### Post by wojox on 2011-01-15
What is in it, Broadcom? Run this and post back the details:

```
lspci | grep -i net
```

---

### Post by wep940 on 2011-01-15
With laptops, some of the internal wireless cards are actually connected to an internal USB buss.  So, please also add the output of the following just in case it's needed:
 
lsusb

---

### Post by PaulHA2 on 2011-01-15
Decided to re-install and re-run the driver update--fixed it. Thanks.

---

