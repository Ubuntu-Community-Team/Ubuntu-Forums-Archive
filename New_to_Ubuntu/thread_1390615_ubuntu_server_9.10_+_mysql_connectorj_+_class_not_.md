---
title: "ubuntu server 9.10 + mysql connectorj + class not found"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by joarobles on 2010-01-25
hi, this is my first post.
I've just installed ubuntu server plus Java:
```

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) 64-Bit Server VM (build 14.1-b02, mixed mode)
```i've copied java-connectorJ complete folder for MySQL to /home/joaquin/connectorj
and my CLASSPATH environmental variable (defined in /etc/profile) is

```
joaquin@ubuntu-server:~$ echo $CLASSPATH
.:/home/joaquin/connectorj/mysql-connector-java-5.1.7-bin.jar
```and this JAR file exists...

so i tried to execute the following line:
```

Class.forName("com.mysql.jdbc.Driver");
```but I always obtain the ClassNotFound Exception... any idea? thanks!

---

