---
title: "Error connecting to MySQL server (installed with LAMP)"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by SKYDOS_2 on 2009-05-26
i have this error when  i am trying to open phpmyadmin (screen):
[http://pic.ipicture.ru/uploads/090526/STmlkp77F6.png](http://pic.ipicture.ru/uploads/090526/STmlkp77F6.png) :(

---

### Post by SKYDOS on 2009-05-26
i have this problem (screen): [http://pic.ipicture.ru/uploads/090526/Zo0HMMKNX1.png](http://pic.ipicture.ru/uploads/090526/Zo0HMMKNX1.png)
help please!

---

### Post by cariboo on 2009-05-26
Is mysql running? To make sure open an Applications-->Accessories-->Terminal and type:

```
ps ax | grep mysql
```

the result of the above command should look something like this:

```
 ps ax | grep mysql
18854 pts/0    S+     0:00 grep mysql
23434 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
23473 ?        Sl     0:10 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
23475 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
```

---

### Post by SKYDOS on 2009-05-26
HELP!! please!

---

### Post by SKYDOS on 2009-05-26
no, look what i have:

3871 pts/0  R+  0:00 grep mysql

---

### Post by Elfy on 2009-05-26
Please do not post duplicates - threads merged.

---

### Post by pspsampsp on 2009-05-26
try using root as the username

---

### Post by SKYDOS on 2009-05-26
> **pspsampsp said:**
> try using root as the username

password?

---

### Post by SKYDOS on 2009-05-26
and when i try to run mysql i have this error
[http://pic.ipicture.ru/uploads/090526/V7oOgaRV1S.png](http://pic.ipicture.ru/uploads/090526/V7oOgaRV1S.png)

---

### Post by SKYDOS on 2009-05-26
COOL!!!! 
i have solved this problem just by doing such thing:
sudo apt-get install mysql-server

and it's working)) stupid mistake) thank all)

---

### Post by SKYDOS on 2009-05-26
but now i have another trouble... :(((
my phpmyadmin works ONLY when i am connected to the Internet!
when i turn it off i get from firefox: [http://pic.ipicture.ru/uploads/090526/22879/4RlyUgRpYn.png](http://pic.ipicture.ru/uploads/090526/22879/4RlyUgRpYn.png)
if first image wont load [http://img25.imageshack.us/img25/9963/screenshotmto.png](http://img25.imageshack.us/img25/9963/screenshotmto.png)

---

### Post by mcduck on 2009-05-26
That's a know issue with Network Manager & Firefox. By default Firefox uses information from Network manager to decide if the machine is online or not, and switches automatically to offline mode if Network manager isn't connected. Of course when connecting to local server you don't need Network Manger to have any connection..

To fix that, type "about:config" in the address bar (in Firefox), use "networkmanager" as filter to find the key "toolkit.networkmanager.disable", right-click it and select "toggle" from the menu to change the key's value to "true". Problem solved. :)

---

### Post by SKYDOS on 2009-05-26
> **mcduck said:**
> That's a know issue with Network Manager & Firefox. By default Firefox uses information from Network manager to decide if the machine is online or not, and switches automatically to offline mode if Network manager isn't connected. Of course when connecting to local server you don't need Network Manger to have any connection..

To fix that, type "about:config" in the address bar (in Firefox), use "networkmanager" as filter to find the key "toolkit.networkmanager.disable", right-click it and select "toggle" from the menu to change the key's value to "true". Problem solved. :)

:popcorn: it's working! many-many-many thanks)

---

### Post by SKYDOS on 2009-05-26
more easier solution:
just open File -> Work Offline    deselect it and reload the page. ) it's working too :)

---

### Post by mcduck on 2009-05-26
> **SKYDOS said:**
> more easier solution:
just open File -> Work Offline    deselect it and reload the page. ) it's working too :)

It works but you have to repeat it every time. Disabling the feature from about:config is a a permanent fix.

---

### Post by SKYDOS on 2009-05-27
> **mcduck said:**
> It works but you have to repeat it every time. Disabling the feature from about:config is a a permanent fix.

yep) you are right! ;)

---

