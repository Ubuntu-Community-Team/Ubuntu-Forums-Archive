---
title: "vsftpd problem"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Vexiphne on 2010-08-25
Can someone please tell me how I can configure vsftpd to use the same directory for all users? 

When someone logs in I want the user to log in to /media/ftphd/files :)

I also have a small problem when starting vsftp. It says:

> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start vsftpd


What does that mean?

---

### Post by stmiller on 2010-08-25
It looks like you can do this with the local_root option in the config file:
> 
local_root
This option represents a directory which vsftpd will try to change into after a local (i.e. non-anonymous) login. Failure is silently ignored.
Default: (none)


Specify a directory for all there, and make sure that directory is readable/writable by all of your ftp users.

This could be a security concern if someone uploads a malicious file or script to execute though. Be careful!

----

> Rather than invoking init scripts through /etc/init.d, use the service(
utility, e.g. service vsftpd start

That means rather than issuing:
```

sudo /etc/init.d/vsftpd start

```
you can do:
```

sudo service vsftpd start

```

---

### Post by Vexiphne on 2010-08-26
Thank you stmiller :)

---

