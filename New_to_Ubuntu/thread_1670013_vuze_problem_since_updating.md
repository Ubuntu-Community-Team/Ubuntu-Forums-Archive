---
title: "vuze problem since updating"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by grouchyolddude on 2011-01-18
I just recently upgraded to 10.10 and am having a few issues with some things... one being vuze. It failed to launch, so I tried sudo apt-get remove --purge vuze. Then sudo apt-get install vuze. 
I'm getting this error when I try to launch. 
   


> o@o-desktop:~$ vuze
[warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/o/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Listener
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:111)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
	... 12 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Listener
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at com.aelitis.azureus.launcher.classloading.PrimaryClassloader.loadClass(PrimaryClassloader.java:103)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 15 more
Start fails:
com.aelitis.azureus.core.AzureusCoreException: Azureus core already instantiated
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:120)
	at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:160)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)


---

### Post by grouchyolddude on 2011-01-18
....(bump).....
 been muckin' with this for a couple of hours now. removed and reinstalled azureous and vuze. reinstalled vuze from command line.Lookin' and reading...
 Still getting the error

---

