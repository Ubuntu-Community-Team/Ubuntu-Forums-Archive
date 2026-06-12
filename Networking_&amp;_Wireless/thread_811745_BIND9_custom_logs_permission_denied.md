---
title: "BIND9 custom logs permission denied"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by binary.koala on 2008-05-29
hi those how dig bind,

i was just trying to setup some custom logging for my BIND9 and failed:

```

May 29 17:28:33 blast named[10924]: logging channel 'query' file '/var/log/query.log': permission denied

```

permissions on log file is:
```

 -rw-r--r-- 1 bind root 0 2008-05-29 17:26 query.log

```

according to [https://help.ubuntu.com/community/BIND9ServerHowto#head-44482c079ef8876038306d99db040e1fcb9ea535](https://help.ubuntu.com/community/BIND9ServerHowto#head-44482c079ef8876038306d99db040e1fcb9ea535) it supposed to work.

i tried also setting log directory as /tmp - same result. 
i'm on 8.04 x32, BIND 9.4.2

any clues?

somewhat feels like a similar issue with SElinux: [http://www.isc.org/index.pl?/sw/bind/FAQ.php](http://www.isc.org/index.pl?/sw/bind/FAQ.php) (search for "custom logs")

---

### Post by denrober on 2008-10-21
I had the same problem today.  It was "AppArmor" which is like SE Linux.  You need to edit /etc/apparmor.d/usr.sbin.named and give it permissions to write to the directory where your log file is.

Mine looks like:

  /var/log/dns/** rw,

Restart apparmor and then bind and it should work.

---

### Post by binary.koala on 2008-10-21
right

---

