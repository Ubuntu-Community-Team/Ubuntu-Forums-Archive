---
title: "Randomly freezes"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by kyeh on 2009-03-06
Hello, i have a desktop-server running on one of my boxes, it is usually on for weeks without a restart.

What the problem is, the computer just suddenly "stops" - this varies from 1 day to a week.

The screen won't get any input (monitor light stays yellow), the keyboard and mouse don't respond. the only thing i can do is press the power button.

It has happened on fluxbox and gnome (havn't tried other ones).

Any ideas why it's doing this?

Running: hardy, some scripts, file sharing.

---

### Post by utnubuuser on 2009-03-06
something in the bios?

Scan your syslogs for messages/events

---

### Post by Vince4Amy on 2009-03-06
Yes check the logs. Also if you have the space or any other install media try just running a clean (Fully Updated) install to see if the same thing happens if not then it must be something you've added to the system.

---

### Post by kyeh on 2009-03-06
These logs are from just before it last crashed

**Syslog**
```

Mar  6 12:10:01 SERVER /USR/SBIN/CRON[5299]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Mar  6 12:10:02 SERVER sendmail[5308]: My unqualified host name (SERVER) unknown; sleeping for retry
Mar  6 12:10:53 SERVER winbindd[7809]: [2009/03/06 12:10:53, 0] nsswitch/idmap.c:idmap_alloc_init(750)
Mar  6 12:10:53 SERVER winbindd[7809]:   ERROR: Initialization failed for alloc backend, deferred!
Mar  6 12:10:53 SERVER smbd[5502]: [2009/03/06 12:10:53, 0] auth/auth_util.c:create_builtin_administrators(792)
Mar  6 12:10:53 SERVER smbd[5502]:   create_builtin_administrators: Failed to create Administrators
Mar  6 12:10:53 SERVER winbindd[7809]: [2009/03/06 12:10:53, 0] nsswitch/idmap.c:idmap_alloc_init(750)
Mar  6 12:10:53 SERVER winbindd[7809]:   ERROR: Initialization failed for alloc backend, deferred!
Mar  6 12:10:53 SERVER smbd[5502]: [2009/03/06 12:10:53, 0] auth/auth_util.c:create_builtin_users(758)
Mar  6 12:10:53 SERVER smbd[5502]:   create_builtin_users: Failed to create Users
Mar  6 12:10:53 SERVER winbindd[5503]: [2009/03/06 12:10:53, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Mar  6 12:10:53 SERVER winbindd[5503]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend
Mar  6 12:10:53 SERVER winbindd[5503]: [2009/03/06 12:10:53, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
Mar  6 12:10:53 SERVER winbindd[5503]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
Mar  6 12:11:02 SERVER sendmail[5308]: unable to qualify my own domain name (SERVER) -- using short name
Mar  6 12:11:02 SERVER sendmail[5308]: n261B2HI005308: from=root, size=356, class=0, nrcpts=1, msgid=<200903060111.n261B2HI005308@SERVER>, relay=root@localhost
Mar  6 12:11:02 SERVER sm-mta[5513]: n261B2dO005513: from=<root@SERVER>, size=582, class=0, nrcpts=1, msgid=<200903060111.n261B2HI005308@SERVER>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Mar  6 12:11:02 SERVER sendmail[5308]: n261B2HI005308: to=root, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30356, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (n261B2dO005513 Message accepted for delivery)
Mar  6 12:11:02 SERVER sm-mta[5514]: n261B2dO005513: to=server, ctladdr=<root@SERVER> (0/0), delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30771, dsn=2.0.0, stat=Sent

```

**cat messages | grep "Mar  6 12"**
```

Mar  6 12:08:02 SERVER -- MARK --

```

**kern.log** - gave nothing other than boot time messages

---

