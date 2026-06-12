---
title: "GCALDaemon"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by siehtschlecht on 2007-03-05
I´ve installed GCALDaemon from thishttp://gcaldaemon.sourceforge.net/. in my folder /usr/local/sbin/GCALDaemon/bin i have standalone-start.sh
But when i type standalone-start.sh i get: bash: standalone-start.sh: command not found.
Why?
I need help please.

---

### Post by Incie83 on 2007-03-09
Did you just type 

> standalone-start.sh

? 

If so, you should've typed:

```
./standalone-start.sh
```

---

### Post by siehtschlecht on 2007-03-13
Thank you, that works! But now another problem.
Installation went fine, but tha i get this:
INFO  | GCALDaemon V1.0 beta 6 starting...
INFO  | HTTP server starting on port 9090...
INFO  | RSS/ATOM feed converter enabled.
INFO  | HTTP server started successfully.
INFO  | Start listening file /usr/local/sbin/GCALDaemon/google.ics...
INFO  | File listener started successfully.
INFO  | LDAP server starting on port 9080...
INFO  | LDAP server started successfully.
INFO  | Gmail notifier disabled.
INFO  | Sendmail service disabled.
INFO  | Mail terminal disabled.
WARN  | Connection refused (localhost.localdomain is a forbidden hostname)!
ERROR | Unable to load calendar!
java.lang.Exception: Invalid iCal file: [http://www.google.com/calendar/ical/example%40gmail.com/private-495cf94a5c0f1bfg/basic.ics](http://www.google.com/calendar/ical/example%40gmail.com/private-495cf94a5c0f1bfg/basic.ics)
        at org.gcaldaemon.core.GCalUtilities.loadCalendar(GCalUtilities.java:179)
        at org.gcaldaemon.core.Configurator.getCalendar(Configurator.java:565)
        at org.gcaldaemon.core.file.FileListener.run(FileListener.java:219)
WARN  | Connection refused, forbidden hostname (localhost.localdomain)!
java.lang.Exception: Connection refused, forbidden hostname (localhost.localdomain)!
        at org.gcaldaemon.core.ldap.LDAPListener.processAccept(LDAPListener.java:248)
        at org.gcaldaemon.core.ldap.LDAPListener.run(LDAPListener.java:184)
WARN  | Connection refused (localhost.localdomain is a forbidden hostname)!
WARN  | Connection refused (localhost.localdomain is a forbidden hostname)!

What means localhost.localdomain is a forbidden hostname?
Thank you.

---

### Post by rfdeshon on 2007-07-28
Please follow the instructions on the GCALdaemon site. The private address in the config file should not have the "http://www.google.com" part on it, just the /calendar/ical.... etc part

---

### Post by dc.wolfpack on 2007-12-13
I am having a similiar problem when running standalone-start.sh; this is the output:

log4j:ERROR Unable to init logger!
java.io.FileNotFoundException: /usr/local/sbin/GCALDaemon/bin/../log/gcal-daemon.log (Permission denied)
        at java.io.RandomAccessFile.open(Native Method)
        at java.io.RandomAccessFile.<init>(RandomAccessFile.java:212)
        at org.gcaldaemon.logger.FileChannelAppender.activateOptions(FileChannelAppender.java:130)
        at org.apache.log4j.config.PropertySetter.activate(PropertySetter.java:247)
        at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:123)
        at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:87)
        at org.apache.log4j.PropertyConfigurator.parseAppender(PropertyConfigurator.java:645)
        at org.apache.log4j.PropertyConfigurator.parseCategory(PropertyConfigurator.java:603)
        at org.apache.log4j.PropertyConfigurator.configureRootCategory(PropertyConfigurator.java:500)
        at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:406)
        at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:307)
        at org.apache.log4j.PropertyConfigurator.configure(PropertyConfigurator.java:315)
        at org.gcaldaemon.core.Configurator.<init>(Configurator.java:277)
        at org.gcaldaemon.standalone.Main.main(Main.java:46)
log4j:WARN Please check the file permissions on the 'log' folder!
Hint: [sudo] chmod -R 777 /usr/local/sbin/GCALDaemon/bin/..
INFO  | GCALDaemon V1.0 beta 14 starting...
INFO  | RSS/ATOM feed converter enabled.
INFO  | Local time zone is Eastern Standard Time.
INFO  | HTTP server starting on port 9090...
FATAL | ADDRESS ALREADY IN USE
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
        at org.gcaldaemon.core.Configurator.startService(Configurator.java:706)
        at org.gcaldaemon.core.Configurator.<init>(Configurator.java:620)
        at org.gcaldaemon.standalone.Main.main(Main.java:46)
Caused by: java.net.BindException: Address already in use
        at java.net.PlainSocketImpl.socketBind(Native Method)
        at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:359)
        at java.net.ServerSocket.bind(ServerSocket.java:319)
        at java.net.ServerSocket.<init>(ServerSocket.java:185)
        at java.net.ServerSocket.<init>(ServerSocket.java:97)
        at org.gcaldaemon.core.http.HTTPListener.<init>(HTTPListener.java:117)
        ... 7 more
FATAL | Service terminated!
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
        at org.gcaldaemon.core.Configurator.startService(Configurator.java:706)
        at org.gcaldaemon.core.Configurator.<init>(Configurator.java:620)
        at org.gcaldaemon.standalone.Main.main(Main.java:46)
Caused by: java.net.BindException: Address already in use
        at java.net.PlainSocketImpl.socketBind(Native Method)
        at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:359)
        at java.net.ServerSocket.bind(ServerSocket.java:319)
        at java.net.ServerSocket.<init>(ServerSocket.java:185)
        at java.net.ServerSocket.<init>(ServerSocket.java:97)
        at org.gcaldaemon.core.http.HTTPListener.<init>(HTTPListener.java:117)
        ... 7 more

help please!

---

