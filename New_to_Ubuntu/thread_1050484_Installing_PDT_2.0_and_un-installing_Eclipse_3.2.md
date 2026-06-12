---
title: "Installing PDT 2.0 and un-installing Eclipse 3.2"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Xeoncross on 2009-01-25
**[COLOR="Red"]UPDATE: *Solved*[/COLOR]** duh, I kept getting the generic eclipse downloads and not the "x64" ones. With the 64x ed. eclipse 3.4 runs fine - now to download the PDT add-on (which it is doing as I speak).



I tried to download the PDT all-in-one from eclipse and found that it wouldn't start (later I learned it had something to do with Ubuntu's default JAVA vm). Anyway, I saw Eclipse listed in the app directory so I clicked on it and installed it instead.

However, it seems to be the old 3.2 version that doesn't work with PDT 2.

So I decided to try to uninstall it and manually install PDT all-in-one again - but the add/remove apps won't let me! It says that I have to use "synaptics" which I hadn't seen anywhere.

Anyway, I figured it must be somewhere so I lunched the cmd prompt and typed in "sudo synaptics" and it pulled the the package manager. But when I selected eclipse for "full removal" it doesn't seem to list the other addon/plugin libraries for removal. I guess that I have to figure out where and what they all are!?

So what am I doing wrong and where should I be looking? I have only been using Ubuntu/linux for about 30hrs at this point.

---

### Post by Xeoncross on 2009-01-25
Wow, F1 pops-up a help menu that actually helps! Maybe M$ should try that approch...

Anyway, the solution to the un-install looks like the command

```

sudo apt-get autoremove eclipse

```

as given in the package manager section of the help docs. Now how do I get PDT 2 installed?...

UPDATE:
I forgot to mention that I am on a 64bit CPU.

Anyway, I have tried Aptana and I can't even get it to work. I'm back to just getting a low level plugin of PDT .07(?) or something - anything - that will give me a better IDE for PHP.

---

### Post by Xeoncross on 2009-01-26
I have tried installing PDT 2.0 standalone - no response/error/nothing
I have tried installing PDT plugin - errors about not having the right components on Eclipse.

I have tried installing Aptana Standalone - finally got an error
```

!SESSION 2009-01-26 17:50:45.957 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.6.0_0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.osgi 4 0 2009-01-26 17:50:47.190
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/owner/.Aptana/Aptana Studio/configuration/org.eclipse.osgi/bundles/28/1/.cp/libswt-pi-gtk-3236.so: /home/owner/.Aptana/Aptana Studio/configuration/org.eclipse.osgi/bundles/28/1/.cp/libswt-pi-gtk-3236.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
    at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
    at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
    at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
    at com.aptana.ide.rcp.AbstractIDEApplication.createDisplay(AbstractIDEApplication.java:152)
    at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:89)
    at com.aptana.ide.rcp.Application.run(Application.java:57)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2009-01-26 17:50:47.233
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-01-26 17:50:47.233
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.2.1.020234.jar was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2009-01-26 17:50:47.234
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0.

!ENTRY org.eclipse.osgi 2 0 2009-01-26 17:50:47.235
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-01-26 17:50:47.235
!MESSAGE Bundle update@plugins/org.tigris.subversion.clientadapter.javahl.win32_1.5.4.jar [24] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-01-26 17:50:47.235
!MESSAGE Bundle update@plugins/com.aptana.ide.xul_1.2.1.020234.jar [57] was not resolved.
!SUBENTRY 2 com.aptana.ide.xul 2 0 2009-01-26 17:50:47.235
!MESSAGE Missing required bundle org.eclipse.atf.mozilla.ide.core_0.0.0. 

```

However, I couldn't get the Aptana plugin to install.

Tried installing Netbeans 6.5 - it works - but it looks horrible. I don't think I would ever want to use something like that. Why are the code lines SO BIG? I think there must be 30px between each line (even though the line-height looks like 19px) and there is no way to change it! Also, the color is all funky for class variables EVEN THOUGH I changed it in options.

---

