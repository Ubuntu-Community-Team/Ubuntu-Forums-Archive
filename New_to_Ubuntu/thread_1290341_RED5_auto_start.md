---
title: "RED5 auto start"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by tagtekin on 2009-10-13
I have Red5 installed on Ubuntu Desktop

i can manually type 

cd /opt/red5/dist/
and then
./red5.sh

and start the application

however i would like this service to start everytime server starts automatically

I tried adding a file myprogram.sh into /etc/init.d/myprogram.sh and inside that i have 

#!/bin/bash
/opt/red5/dist/ ./red5.sh

how ever the error is 

Exception in thread "main" java.lang.ClassNotFoundException: org.red5.server.Launcher
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:247)
        at org.red5.server.Bootstrap.bootStrap(Bootstrap.java:109)
        at org.red5.server.Bootstrap.main(Bootstrap.java:50)

it looks like the JAVA is not executing the program right

any ideas?

---

### Post by jaknap on 2010-09-09
May This help you

[http://pankajdangi.com/2010/09/how-to-auto-start-red5-in-linux-server/](http://pankajdangi.com/2010/09/how-to-auto-start-red5-in-linux-server/)

---

### Post by C4RL0 on 2012-11-09
Did you solve your problem untill now? I receive exactly the same message when I try to start red5 by script.

---

### Post by oldos2er on 2012-11-09
Please start a new thread, this one's quite old.

---

