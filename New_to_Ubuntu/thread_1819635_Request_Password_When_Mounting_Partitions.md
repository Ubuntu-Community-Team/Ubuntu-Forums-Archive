---
title: "Request Password When Mounting Partitions"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2011-08-06
Hello everyone, I'm in the process of migrating my boxes to 11.04 and I realized that Ubuntu no longer asks for a password when mounting other partitions. Is there a way to re-enable this?

Thanks!

---

### Post by ubudog on 2011-08-06
Hi, check this out:
[http://ubuntuforums.org/showthread.php?t=1467629](http://ubuntuforums.org/showthread.php?t=1467629)

(specifically the 4th post)

:-)

---

### Post by Lazy-buntu on 2011-08-06
> **ubudog said:**
> Hi, check this out:
[http://ubuntuforums.org/showthread.php?t=1467629](http://ubuntuforums.org/showthread.php?t=1467629)

(specifically the 4th post)

:-)


Perfect! Thanks! For those interested:

> **mc4man said:**
> In a terminal go 
```
gksu gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```

For the first listed override change the ResultActive=yes to

ResultActive=auth_admin_keep


---

### Post by ubudog on 2011-08-06
No problem!  :-)

---

