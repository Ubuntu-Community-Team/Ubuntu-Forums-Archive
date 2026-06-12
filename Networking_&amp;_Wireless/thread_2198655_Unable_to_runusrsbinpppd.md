---
title: "Unable to run/usr/sbin/pppd"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by merlill on 2014-01-09
Here's my situation. I set up an older pc with ubuntu 11.10 to go online with an external modem. All seems to be fine except I get this message when I attempt to connect:

check permissions, or specify a "PPPD Path" option in wvdial.conf.
Don't know what to do! Starting pppd and hoping for the best.
Unable to run/usr/sbin/pppd

There's probably a simple solution but I have not been able to find a way to change permissions. Can anyone help?

merle

---

### Post by ian-weisser on 2014-01-10
```
$ ls -l /usr/sbin/pppd
-rwsr-xr-- 1 root dip 322968 Jan 22  2013 /usr/sbin/pppd
```

If I want to run pppd, I must be a member of the appropriate group. In this case, the dip group.
Are you a member of the appropriate group?

---

### Post by merlill on 2014-01-10
You identified the problem and it is now fixed. Thank you very much for pointing me in the right direction.
Merle

---

