---
title: "Glom DB on Remote Server"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by k33bz on 2010-09-19
I figured out how to get Glom working on remote server (at least in theory). Did not notice before that I could create on a remote server. Have been playing with it for awhile now.

I keep getting this no matter how I try it

```
Glom could not connect to the database server. Maybe you entered an incorrect user name or password, or maybe the postgres database server is not running.
```

According to webmin postgres is running, I did everything according to this site [http://www.glom.org/wiki/index.php?title=Initial_Postgres_Configuration]("http://www.glom.org/wiki/index.php?title=Initial_Postgres_Configuration")

I tried the local networks IP with and without defining a port (according to the configs postgres runs on 5432). Also port forwarded 5432 on my router to the server and tried my IP address with and with out defining a port.

But I always get the same thing.

---

