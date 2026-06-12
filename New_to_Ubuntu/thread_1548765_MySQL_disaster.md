---
title: "MySQL disaster"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by auroraa9420 on 2010-08-08
I had some problems with my sql that is that i cannot acsess it even if i reinstalled it and everything

i use the MySQL Query Browser and it seem to kick out a message

Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Click the 'Ping' button to see if there is a networking problem.

autologicly i thougth that it had something to do with ports or network connectivity

---

### Post by sandyd on 2010-08-08
> **auroraa9420 said:**
> I had some problems with my sql that is that i cannot acsess it even if i reinstalled it and everything

i use the MySQL Query Browser and it seem to kick out a message

Could not connect to host 'localhost'.
MySQL Error Nr. 2002
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Click the 'Ping' button to see if there is a networking problem.

autologicly i thougth that it had something to do with ports or network connectivitydid you install the mysql-server package?

---

### Post by auroraa9420 on 2010-08-08
> **carlee said:**
> did you install the mysql-server package?

yes i did...and still i resieved the same message :(

---

### Post by sandyd on 2010-08-08
> **auroraa9420 said:**
> yes i did...and still i resieved the same message :(
post the output of
```

/etc/init.d/mysqld start
ls /var/run/mysqld

```

---

### Post by auroraa9420 on 2010-08-08
> **carlee said:**
> post the output of
```

/etc/init.d/mysqld start
ls /var/run/mysqld

```

there was no mysqld in the 
[FONT=monospace]
[/FONT]/etc/init.d/
and the secound line (ls) was empty

---

### Post by sandyd on 2010-08-08
typo
meant
```

sudo /etc/init.d/mysql restart
```

---

### Post by auroraa9420 on 2010-08-08
> **carlee said:**
> typo
meant
```

sudo /etc/init.d/mysql restart
```\

wow thanks :D

---

