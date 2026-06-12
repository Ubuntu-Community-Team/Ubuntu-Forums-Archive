---
title: "Eclipse not working!"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by igriego on 2009-06-19
when i try loading Eclipse i get:

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 80800d
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

---

### Post by porchrat on 2009-06-19
Have you tried installing the Sun JDK?

That gcj is not 100% compatible and I have experienced problems with it in the past.

Go into synaptic and download the Sun JDK.

Then use the "update-alternatives" command to set Sun's jre and javac as default.

For the JRE:
```
sudo update-alternatives --config java
```

For the javac:
```
sudo update-alternatives --config javac
```

Once you enter that command you can select the Sun 1.6 option from the list and hopefully that will help.

---

