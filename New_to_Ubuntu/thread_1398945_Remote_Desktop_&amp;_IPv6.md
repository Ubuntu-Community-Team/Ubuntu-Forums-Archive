---
title: "Remote Desktop &amp; IPv6"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by spikoley on 2010-02-05
I am using Remote Desktop to VNC into an Ubuntu box.  When running it from a shell it shows its using IPv6.  I am guessing that is causing the connection issue.

```

05/02/2010 02:03:06 AM [IPv6] Got connection from client ::ffff:192.168.1.3
05/02/2010 02:03:06 AM   other clients:
05/02/2010 02:03:06 AM      ::ffff:192.168.1.3
05/02/2010 02:03:06 AM      ::ffff:192.168.1.3
05/02/2010 02:03:06 AM      ::ffff:192.168.1.3
05/02/2010 02:03:06 AM      ::ffff:192.168.1.3

```
 
Could IPv6 cause this issue or could this be on the client end?  On the client end I receive "connection failed"

Any ideas?

---

### Post by spikoley on 2010-02-05
Its working now.  I enabled Remote Desktop under Startup Applications and rebooted instead of running it from the shell.

---

