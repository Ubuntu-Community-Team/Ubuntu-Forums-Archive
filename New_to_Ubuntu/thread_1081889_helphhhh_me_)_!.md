---
title: "helphhhh me :) !"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by mash.ky on 2009-02-27
i installed tomcat 5.5 into my ubuntu 8.10 and when i run startup.sh it works fine. but when i run shutdown.sh it gives ```
ushan@ubuntu:~$ /var/lib/tomcat5.5/bin/shutdown.sh
Using CATALINA_BASE:   /var/lib/tomcat5.5
Using CATALINA_HOME:   /var/lib/tomcat5.5
Using CATALINA_TMPDIR: /var/lib/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.17/jre/
java.lang.ClassNotFoundException: org.apache.catalina.startup.Catalina
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.apache.catalina.startup.Bootstrap.init(Bootstrap.java:222)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:410)

```

how to solve this prob? 


and when i run [http://localhost:8080](http://localhost:8080) or 8180 it doesn't work. what shall i do?

---

### Post by hyperyoda on 2009-02-27
> **mash.ky said:**
> i installed tomcat 5.5 into my ubuntu 8.10 and when i run startup.sh it works fine. but when i run shutdown.sh it gives ```
ushan@ubuntu:~$ /var/lib/tomcat5.5/bin/shutdown.sh
Using CATALINA_BASE:   /var/lib/tomcat5.5
Using CATALINA_HOME:   /var/lib/tomcat5.5
Using CATALINA_TMPDIR: /var/lib/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.17/jre/
java.lang.ClassNotFoundException: org.apache.catalina.startup.Catalina
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.apache.catalina.startup.Bootstrap.init(Bootstrap.java:222)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:410)

```

how to solve this prob? 


and when i run [http://localhost:8080](http://localhost:8080) or 8180 it doesn't work. what shall i do?


Try this: [http://www.jguru.com/faq/view.jsp?EID=40691]("http://www.jguru.com/faq/view.jsp?EID=40691")

This mailing list might be able to assist you. Send a message to:
[email]tomcat-user-subscribe@jakarta.apache.org[/email]

Zach

---

