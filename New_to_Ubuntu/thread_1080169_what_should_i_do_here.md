---
title: "what should i do here?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by mash.ky on 2009-02-25
i hav installed tomcat 5.5 successfully in to my ubuntu 8.10 machine. when i ran tomcat as root it worked well. but when i start tomcat as user it worked well. but when i tried to stop it, it gave some errors. just hav alook >>>>```
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
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /var/lib/tomcat5.5/logs/catalina.2009-02-25.log (Permission denied)
	at java.io.FileOutputStream.openAppend(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:177)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:102)
	at java.io.FileWriter.<init>(FileWriter.java:61)
	at org.apache.juli.FileHandler.open(FileHandler.java:259)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:59)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:50)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at java.lang.Class.newInstance0(Class.java:350)
	at java.lang.Class.newInstance(Class.java:303)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:396)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:341)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:237)
	at java.util.logging.LogManager$2.run(LogManager.java:258)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:256)
	at java.util.logging.LogManager.getLogManager(LogManager.java:239)
	at java.util.logging.Logger.<init>(Logger.java:201)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:973)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:970)
	at java.util.logging.LogManager$1.run(LogManager.java:179)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.<clinit>(LogManager.java:156)
	at java.util.logging.Logger.getLogger(Logger.java:254)
	at org.apache.commons.logging.impl.Jdk14Logger.getLogger(Jdk14Logger.java:152)
	at org.apache.commons.logging.impl.Jdk14Logger.<init>(Jdk14Logger.java:53)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at org.apache.commons.logging.impl.LogFactoryImpl.newInstance(LogFactoryImpl.java:529)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:235)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:209)
	at org.apache.commons.logging.LogFactory.getLog(LogFactory.java:351)
	at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:54)
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /var/lib/tomcat5.5/logs/localhost.2009-02-25.log (Permission denied)
	at java.io.FileOutputStream.openAppend(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:177)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:102)
	at java.io.FileWriter.<init>(FileWriter.java:61)
	at org.apache.juli.FileHandler.open(FileHandler.java:259)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:59)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:50)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at java.lang.Class.newInstance0(Class.java:350)
	at java.lang.Class.newInstance(Class.java:303)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:396)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:341)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:237)
	at java.util.logging.LogManager$2.run(LogManager.java:258)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:256)
	at java.util.logging.LogManager.getLogManager(LogManager.java:239)
	at java.util.logging.Logger.<init>(Logger.java:201)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:973)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:970)
	at java.util.logging.LogManager$1.run(LogManager.java:179)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.<clinit>(LogManager.java:156)
	at java.util.logging.Logger.getLogger(Logger.java:254)
	at org.apache.commons.logging.impl.Jdk14Logger.getLogger(Jdk14Logger.java:152)
	at org.apache.commons.logging.impl.Jdk14Logger.<init>(Jdk14Logger.java:53)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at org.apache.commons.logging.impl.LogFactoryImpl.newInstance(LogFactoryImpl.java:529)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:235)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:209)
	at org.apache.commons.logging.LogFactory.getLog(LogFactory.java:351)
	at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:54)
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /var/lib/tomcat5.5/logs/manager.2009-02-25.log (Permission denied)
	at java.io.FileOutputStream.openAppend(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:177)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:102)
	at java.io.FileWriter.<init>(FileWriter.java:61)
	at org.apache.juli.FileHandler.open(FileHandler.java:259)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:59)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:50)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at java.lang.Class.newInstance0(Class.java:350)
	at java.lang.Class.newInstance(Class.java:303)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:396)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:341)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:237)
	at java.util.logging.LogManager$2.run(LogManager.java:258)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:256)
	at java.util.logging.LogManager.getLogManager(LogManager.java:239)
	at java.util.logging.Logger.<init>(Logger.java:201)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:973)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:970)
	at java.util.logging.LogManager$1.run(LogManager.java:179)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.<clinit>(LogManager.java:156)
	at java.util.logging.Logger.getLogger(Logger.java:254)
	at org.apache.commons.logging.impl.Jdk14Logger.getLogger(Jdk14Logger.java:152)
	at org.apache.commons.logging.impl.Jdk14Logger.<init>(Jdk14Logger.java:53)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at org.apache.commons.logging.impl.LogFactoryImpl.newInstance(LogFactoryImpl.java:529)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:235)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:209)
	at org.apache.commons.logging.LogFactory.getLog(LogFactory.java:351)
	at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:54)
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /var/lib/tomcat5.5/logs/admin.2009-02-25.log (Permission denied)
	at java.io.FileOutputStream.openAppend(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:177)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:102)
	at java.io.FileWriter.<init>(FileWriter.java:61)
	at org.apache.juli.FileHandler.open(FileHandler.java:259)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:59)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:50)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at java.lang.Class.newInstance0(Class.java:350)
	at java.lang.Class.newInstance(Class.java:303)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:396)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:341)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:237)
	at java.util.logging.LogManager$2.run(LogManager.java:258)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:256)
	at java.util.logging.LogManager.getLogManager(LogManager.java:239)
	at java.util.logging.Logger.<init>(Logger.java:201)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:973)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:970)
	at java.util.logging.LogManager$1.run(LogManager.java:179)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.<clinit>(LogManager.java:156)
	at java.util.logging.Logger.getLogger(Logger.java:254)
	at org.apache.commons.logging.impl.Jdk14Logger.getLogger(Jdk14Logger.java:152)
	at org.apache.commons.logging.impl.Jdk14Logger.<init>(Jdk14Logger.java:53)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at org.apache.commons.logging.impl.LogFactoryImpl.newInstance(LogFactoryImpl.java:529)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:235)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:209)
	at org.apache.commons.logging.LogFactory.getLog(LogFactory.java:351)
	at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:54)
java.util.logging.ErrorManager: 4
java.io.FileNotFoundException: /var/lib/tomcat5.5/logs/host-manager.2009-02-25.log (Permission denied)
	at java.io.FileOutputStream.openAppend(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:177)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:102)
	at java.io.FileWriter.<init>(FileWriter.java:61)
	at org.apache.juli.FileHandler.open(FileHandler.java:259)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:59)
	at org.apache.juli.FileHandler.<init>(FileHandler.java:50)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at java.lang.Class.newInstance0(Class.java:350)
	at java.lang.Class.newInstance(Class.java:303)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:396)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:341)
	at org.apache.juli.ClassLoaderLogManager.readConfiguration(ClassLoaderLogManager.java:237)
	at java.util.logging.LogManager$2.run(LogManager.java:258)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.readPrimordialConfiguration(LogManager.java:256)
	at java.util.logging.LogManager.getLogManager(LogManager.java:239)
	at java.util.logging.Logger.<init>(Logger.java:201)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:973)
	at java.util.logging.LogManager$RootLogger.<init>(LogManager.java:970)
	at java.util.logging.LogManager$1.run(LogManager.java:179)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.logging.LogManager.<clinit>(LogManager.java:156)
	at java.util.logging.Logger.getLogger(Logger.java:254)
	at org.apache.commons.logging.impl.Jdk14Logger.getLogger(Jdk14Logger.java:152)
	at org.apache.commons.logging.impl.Jdk14Logger.<init>(Jdk14Logger.java:53)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at org.apache.commons.logging.impl.LogFactoryImpl.newInstance(LogFactoryImpl.java:529)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:235)
	at org.apache.commons.logging.impl.LogFactoryImpl.getInstance(LogFactoryImpl.java:209)
	at org.apache.commons.logging.LogFactory.getLog(LogFactory.java:351)
	at org.apache.catalina.startup.Bootstrap.<clinit>(Bootstrap.java:54)
Feb 25, 2009 3:58:24 PM org.apache.catalina.startup.Catalina stopServer
SEVERE: Catalina.stop: 
java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
	at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
	at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
	at java.net.Socket.connect(Socket.java:520)
	at java.net.Socket.connect(Socket.java:470)
	at java.net.Socket.<init>(Socket.java:367)
	at java.net.Socket.<init>(Socket.java:180)
	at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:395)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:344)
	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:435)
ushan@ubuntu:~$ 

```


how to resolve this error. help me !

---

### Post by yeats on 2009-02-25
Looks like you need to run those commands prefaced by "sudo."  The error is that you do not have permission to access the log file required by each command.

---

### Post by mash.ky on 2009-02-25
as i read some notes on installing tomcat decribed not to use sudo when u r running tomcat as user. then it would display an error message. in this case when i run /var/lib/tomcat5.5/bin/startup.sh tomcat starts without any problem. error comes when i stop it. is it involve with the user of tomcat. if so how can i do changes. i'm newbie to linux. indetail explananions would be very helpful. thanx cris.

---

### Post by Bölvaður on 2009-02-25
I may be blind but I only see

/var/lib/tomcat5.5/logs/manager.2009-02-25.log (Permission denied)
/var/lib/tomcat5.5/logs/admin.2009-02-25.log (Permission denied)
/var/lib/tomcat5.5/logs/host-manager.2009-02-25.log (Permission denied)

What you need to do is change the access of those files or the entire directory to allow others to write. Or rather perhaps, to change this directory to be owned by the user.

<warning>I have no idea if it is wise or not security wise, I have yet to run apache server and have no idea how they do things. I do not have this directory so I have no idea what else is contained in there so I have no idea if you would want your user to be able to access and change them</warning>


<another warning>I will use the -R flag which will recursively execute the command on all files and directories so make sure not to use R if you have other directories that you do not want to be affected.</another warning>
open up the terminal
```

sudo chown **mash.ky** /var/lib/tomcat5.5/logs/ -R
```

also if there are still issues then you may need to change the permission to allow the user to read/write/execute
```
sudo chmod u=rwx /var/lib/tomcat5.5/logs/ -R
```

---

### Post by mash.ky on 2009-02-25
greate help bol. now it's working without errors. startup.sh and shutdown.sh works perfect. thanx again dude. :D

---

