---
title: "SquidGuard setup problem."
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by Bengaul on 2007-07-18
Hello, 

Trying to set up squidGuard, and am stuck with one issue I am unable to fathom. When I do squidGuard -C all, it seems to go OK, and no errors are produced in the log. When I try the squid -k reconfigure I get the error;

root@ubu:/usr/bin# squid -k reconfigure
squid: ERROR: Could not send signal 1 to process 3896: (3) No such process

Does anyone have any ideas?

Thanks in advance.

---

### Post by Sarisar on 2007-07-19
The squid -k reconfigure command should stop and restart the service.  Looks like it's having trouble finding it.

Have a look in /etc/init.d and see if squid is mentioned there
```

ls /etc/init.d/squid
```

That should show
```
/etc/init.d/squid
```

I'm guessing it's not... but I may be wrong.

---

