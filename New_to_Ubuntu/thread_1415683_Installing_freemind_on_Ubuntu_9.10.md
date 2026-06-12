---
title: "Installing freemind on Ubuntu 9.10"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by Suparna on 2010-02-25
Hi! I am trying to install freemind on Ubuntu 9.10. I tried something looking at various threads on the net. and now I am getting the following response. Please guide me step by step in tutorial form on what to do. Thanks.

suparna@suparna-laptop:~$ sudo apt-get install freemind
[sudo] password for suparna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  freemind-plugins-help freemind-plugins-svg freemind-plugins-script
  freemind-browser
The following NEW packages will be installed:
  freemind
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/2,509kB of archives.
After this operation, 3,273kB of additional disk space will be used.
Selecting previously deselected package freemind.
(Reading database ... 269271 files and directories currently installed.)
Unpacking freemind (from .../freemind_0.9.0~rc6+dfsg-1_all.deb) ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up freemind (0.9.0~rc6+dfsg-1) ...

suparna@suparna-laptop:~$ freemind
Checking Java Version...
java.io.FileNotFoundException: /home/suparna/.freemind/auto.properties (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at freemind.main.FreeMindStarter.readUsersPreferences(FreeMindStarter.java:136)
    at freemind.main.FreeMindStarter.main(FreeMindStarter.java:56)
Panic! Error while loading default properties.
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1646)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1747)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1664)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
    at java.awt.Component.<clinit>(Component.java:568)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at freemind.main.FreeMindStarter.main(FreeMindStarter.java:61)
suparna@suparna-laptop:~$

---

### Post by mikeyphi on 2010-02-25
Not sure what happened there however, open System/Admin/Synaptic.
Do a search for 'freemind' and then install from there.
If that causes problems please come back again!

---

### Post by Suparna on 2010-02-25
Tried it. Installed all the packages that showed up on freemind. Clicking on freemind icon did not result in anything. Went to terminal and typed freemind. Got the following :
Checking Java Version...
java.io.FileNotFoundException: /home/suparna/.freemind/auto.properties (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at freemind.main.FreeMindStarter.readUsersPreferences(FreeMindStarter.java:136)
    at freemind.main.FreeMindStarter.main(FreeMindStarter.java:56)
Panic! Error while loading default properties.
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1646)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1747)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1664)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
    at java.awt.Component.<clinit>(Component.java:568)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at freemind.main.FreeMindStarter.main(FreeMindStarter.java:61)
suparna@suparna-laptop:~$ 

Any suggestions? There seems to be some problem with java. Not able to figure it out.

Suparna

---

### Post by joshd2189 on 2010-02-25
try sudo apt-get install sun-java6-jre
then install freemind..  the open jre/jdk is still lacking imo, best to just stick with sun (i mean oracle..) as they develop java.

---

### Post by Suparna on 2010-02-25
Will try it and get back to you.
thanks
suparna

---

### Post by Suparna on 2010-02-25
Tried it.  tried to open free mind. Here is the output.
Checking Java Version...
java.io.FileNotFoundException: /home/suparna/.freemind/auto.properties (No such file or directory)
    at java.io.FileInputStream.open(Native Method)
    at java.io.FileInputStream.<init>(FileInputStream.java:137)
    at freemind.main.FreeMindStarter.readUsersPreferences(FreeMindStarter.java:136)
    at freemind.main.FreeMindStarter.main(FreeMindStarter.java:56)
Panic! Error while loading default properties.
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1646)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1747)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1664)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
    at java.awt.Component.<clinit>(Component.java:568)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at freemind.main.FreeMindStarter.main(FreeMindStarter.java:61)
suparna@suparna-laptop:~$

---

### Post by joshd2189 on 2010-02-27
what is the output of: 
```
java -version
```

edit:
you have to make sure that sun's java is the default java on your machine
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by themusicalduck on 2010-02-27
Freemind works fine for me, and these are the java packages I have installed. (When I search for "java" in Ubuntu Software Centre)

Sun Java 6.0 Plugin, Ubuntu restricted extras, Sun Java 6 Runtime, OpenJDK Java 6 Runtime, OpenJDK Java 6 Web Start.

If any of these aren't installed then it might be worth installing it to see if it helps.

---

### Post by Suparna on 2010-03-05
Sorry for not having responded earlier.

I did install java 6 runtime etc. But tell me how do i get to ubuntu software centre? will search for the packages you have mentioned.

as of now freemind icon is visible but not functioning.

thanks.

suparna

---

### Post by Suparna on 2010-03-05
well, it seems to be working now. i did not do anything after my last post!

went to terminal and typed freemind. still showing something not available etc but a new map opens up.

so i guess doing

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

worked!

Suparna

---

