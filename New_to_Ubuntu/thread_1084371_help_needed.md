---
title: "help needed"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by mash.ky on 2009-03-02
i am using ubuntu 8.10 and i installed tomcat . it can be started without any error. but when i shutdown it gives some exception. what shall i do?

```
ushan@ubuntu:~$ /var/lib/tomcat5.5/bin/startup.sh
Using CATALINA_BASE:   /var/lib/tomcat5.5
Using CATALINA_HOME:   /var/lib/tomcat5.5
Using CATALINA_TMPDIR: /var/lib/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.17/
ushan@ubuntu:~$ /var/lib/tomcat5.5/bin/shutdown.sh
Using CATALINA_BASE:   /var/lib/tomcat5.5
Using CATALINA_HOME:   /var/lib/tomcat5.5
Using CATALINA_TMPDIR: /var/lib/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.17/
java.lang.ClassNotFoundException: org.apache.catalina.startup.Catalina
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.apache.catalina.startup.Bootstrap.init(Bootstrap.java:222)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:410)
ushan@ubuntu:~$ 
```

and [http://localhost:8080](http://localhost:8080) or 8180 is not working. help me.

---

### Post by hyperyoda on 2009-03-02
> **mash.ky said:**
> i am using ubuntu 8.10 and i installed tomcat . it can be started without any error. but when i shutdown it gives some exception. what shall i do?

```
ushan@ubuntu:~$ /var/lib/tomcat5.5/bin/startup.sh
Using CATALINA_BASE:   /var/lib/tomcat5.5
Using CATALINA_HOME:   /var/lib/tomcat5.5
Using CATALINA_TMPDIR: /var/lib/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.17/
ushan@ubuntu:~$ /var/lib/tomcat5.5/bin/shutdown.sh
Using CATALINA_BASE:   /var/lib/tomcat5.5
Using CATALINA_HOME:   /var/lib/tomcat5.5
Using CATALINA_TMPDIR: /var/lib/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.17/
java.lang.ClassNotFoundException: org.apache.catalina.startup.Catalina
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.apache.catalina.startup.Bootstrap.init(Bootstrap.java:222)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:410)
ushan@ubuntu:~$ 
```

and [http://localhost:8080](http://localhost:8080) or 8180 is not working. help me.


I replied to your original post. Please don't repost. Just bump your original thread. Thanks.

Zach

---

### Post by mash.ky on 2009-03-02
yes yes. i did as u said. but no good result. i'm still having the problem. even when i run ```
ushan@ubuntu:~$ netstat -plut
``` it gives ```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      -               
tcp        0      0 localhost:www           *:*                     LISTEN      -               
tcp        0      0 localhost:ipp           *:*                     LISTEN      -               
udp        0      0 *:bootpc                *:*                                 -               
udp        0      0 *:mdns                  *:*                                 -               
udp        0      0 *:34417                 *:*                                 -               
ushan@ubuntu:~$
``` it seems the port 8080 is not listening rite. pls help.

---

### Post by mash.ky on 2009-03-02
any help..........

---

