---
title: "dpkg cache open???"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by PoPWiZaRD on 2009-01-14
Hi,

Me, new to UbUntU but trying to figure it out as I am going along...

Trying to do my Auto-Updates one day and it replies with a message from,

E: dpkg interrupted 

I have to "run" dpkg manually and configure a/

Next Message says; 

E: cache open, failed, please report.



Can somebody, please help me through this, I have so far opened "dpkg" but haven't gotten any further, don't know what sort of commands to use.

---

### Post by handydan918 on 2009-01-14
> **PoPWiZaRD said:**
> Hi,

Me, new to UbUntU but trying to figure it out as I am going along...

Trying to do my Auto-Updates one day and it replies with a message from,

E: dpkg interrupted 

I have to "run" dpkg manually and configure a/

Next Message says; 

E: cache open, failed, please report.



Can somebody, please help me through this, I have so far opened "dpkg" but haven't gotten any further, don't know what sort of commands to use.

Open a terminal and do ```
dpkg --configure -a
``` and try your update again. If it still fails, you might also try  ```
apt-get install -f
```

---

### Post by jemate18 on 2009-01-14
Type

```
sudo dpkg --configure -a
```

That should fix it...

---

