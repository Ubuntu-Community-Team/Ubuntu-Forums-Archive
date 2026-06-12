---
title: "unable to start mysql"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by navaneethan on 2010-11-10
navanee@navanee-Vostro-1015:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
navanee@navanee-Vostro-1015:~$ 


I couldn't able too start mysql which is installed in my system;so i couldn't able to run phpmyaadmin

plz suggest??

---

### Post by spikoley on 2010-11-11
It looks like this issue is caused by insufficient privileges.  Try putting *sudo* in front of the command.

```
sudo mysql
```

If that doesn't work then try [this post]("http://ubuntuforums.org/showpost.php?p=3371657&postcount=4").

---

### Post by navaneethan on 2010-11-11
> **spikoley said:**
> It looks like this issue is caused by insufficient privileges.  Try putting *sudo* in front of the command.

```
sudo mysql
```

If that doesn't work then try [this post]("http://ubuntuforums.org/showpost.php?p=3371657&postcount=4").

when i follow this link i got this problem? please fix it

```
navanee@navanee-Vostro-1015:/var/run$ sudo chown mysql:root mysqld
chown: invalid user: `mysql:root'

```

---

### Post by spikoley on 2010-11-12
I don't know what the solution is and nobody else is responding.  Try [searching the error]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=ERROR+2002+(HY000):+Can't+connect+to+local+MySQL+server+through+socket+'/var/run/mysqld/mysqld.sock'+(2)") to see if you can find the solution.

---

