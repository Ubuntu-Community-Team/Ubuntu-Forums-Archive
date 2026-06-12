---
title: "Vuze wont start."
date: 2010-11-19
forum: New to Ubuntu
---

### Post by zi0nee on 2010-11-19
Hey guys

i tried installing vuze from this guide [http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)
but when i try start vuze it get this:

> zi0nee@zi0nee:~$ vuze
Starting Azureus...
Suitable java version found [java = 1.6.0_18]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: Cannot load 32-bit SWT libraries on 64-bit JVM
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to                                                                                                  LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib64/firefox-addons for GRE
        Can not use GRE from /usr/lib64/firefox-addons because it's missing libx                                                                                                 pcom.so.
  checking /usr/lib64/mozilla for GRE
        Can not use GRE from /usr/lib64/mozilla because it's missing libxpcom.so                                                                                                 .
  checking /usr/lib64/xulrunner-addons for GRE
        Can not use GRE from /usr/lib64/xulrunner-addons because it's missing li                                                                                                 bxpcom.so.
  checking /usr/lib64/firefox-3.0.8 for GRE
        Can not use GRE from /usr/lib64/firefox-3.0.8 because it's missing libxp                                                                                                 com.so.
  checking /usr/lib64/xulrunner-1.9.0.19 for GRE
GRE found at /usr/lib64/xulrunner-1.9.0.19.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Di                                                                                                 splay
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuze has better                                                                                                  luck.
setting LD_LIBRARY_PATH to: /usr/lib64/xulrunner-1.9.0.19
setting MOZILLA_FIVE_HOME to: /usr/lib64/xulrunner-1.9.0.19
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/vuze" -Da                                                                                                 zureus.install.path="/opt/vuze" -Dazureus.script="/opt/vuze/azureus" -Dazureus.s                                                                                                 cript.version=2 org.gudy.azureus2.ui.swt.Main
file:/opt/vuze/Azureus2.jar ; file:/opt/vuze/swt.jar ; file:/opt/vuze/
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstruct                                                                                                 orAccessorImpl.java:57)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingC                                                                                                 onstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:114)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:292)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.                                                                                                 java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces                                                                                                 sorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
        at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 6                                                                                                 4-bit JVM
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:197)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:174)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:8                                                                                                 4)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThrea                                                                                                 d.java:63)
        at com.aelitis.azureus.ui.swt.Initializer.<init>(Initializer.java:163)
        ... 12 more
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.
i cant figure out what causes this, anyone got some suggestions? :)

- zi0nee

---

### Post by Zookalicious on 2010-11-19
Unless you desperately need to install Vuze via this method, I would suggest simply typing
```

sudo apt-get install vuze

```
into the terminal. :P 

Also unless you are a big fan of Vuze, I would suggest Deluge or Transmission. I have never found Vuze to be that great.

---

### Post by Forlong on 2011-01-25
I just noticed this as well.
The reason why it fails is this:
```
Browser check failed with: Cannot load 32-bit SWT libraries on 64-bit JVM
```
Seems like the official Vuze installer is broken. It installs the AMD64 version regardless of what OS is in use.

The simple solution is going to sourceforge and decide for yourself what version is suitable for you. I have updated the HowTo accordingly.

---

### Post by bliffle on 2011-02-15
Worked fine for me. I juat used forlongs procedure to install vuze in place of deluge on an old Thinkpad T60 running 9.04.

---

