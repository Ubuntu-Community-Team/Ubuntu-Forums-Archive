---
title: "airport-utils doesnt work on feisty (airport2-config dies)"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by OscarWabbit on 2007-10-07
hi

for my wireless connection i am running with an airport extreme base station.  

the problem is i can not configure the airport base station using the "airport-utils" package from feisty.

when i try to run the command "airport2-config", it just dies.

can anyone help with this please?

thanks





EDIT: its ok, ive got it working, the problem was java runtime 6. it works ok with java runtime 5.

just in case anyone else gets the same problem, this command works:

/usr/lib/jvm/java-1.5.0-sun/jre/bin/java -jar /usr/share/java/airport-utils/Airport2BaseStationConfig.jar

---

### Post by rudasn on 2007-10-23
hey

I am having the same problem. Ubuntu 7.10 cannot find hard disks and printers connected to Airport Extreme, even though the internet connection works as it should.

I installed airport-utils thru synaptic and used terminal to run the app. The command I used is airport2-config and the error message I get is this:

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at airport2config.AirportBaseStationConfigurator.<init>(Unknown Source)
   at airport2config.AirportBaseStationConfigurator.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more

```

Any suggestions? 

Cheers

---

### Post by rudasn on 2007-10-24
> **rudasn said:**
> hey

I am having the same problem. Ubuntu 7.10 cannot find hard disks and printers connected to Airport Extreme, even though the internet connection works as it should.

I installed airport-utils thru synaptic and used terminal to run the app. The command I used is airport2-config and the error message I get is this:

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.81)
   at java.awt.Window.<init>(libgcj.so.81)
   at java.awt.Frame.<init>(libgcj.so.81)
   at javax.swing.JFrame.<init>(libgcj.so.81)
   at airport2config.AirportBaseStationConfigurator.<init>(Unknown Source)
   at airport2config.AirportBaseStationConfigurator.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...6 more

```

Any suggestions? 

Cheers

Alright, it appears that one must have Sun's Java to get airport utilities running (instead of GNU's version). You can install Sun's Java from synaptic (enable metaverse repositories).

So I got the airport utilities running, but I can't connect to the external disk drive connected to airport extreme. I don't know what the problem is. Airport utils can retrieve the base station's name but it says nothing about connecting to disks and setting up printers. The internet connection, through ethernet via airport extreme, works ok.

Any suggestions on how to connect to the hard disk and set up the printer?

Cheers

---

### Post by jgneff on 2007-12-02
I had the same problem on Ubuntu 7.10 (Gutsy Gibbon) -- "airport-config" from the command prompt, for example, would just quit without any messages and without displaying its window.  Sun Java 6 Update 3 (version 1.6.0_03) was the default on my system.

I installed the Sun Java 5 JDK "sun-java5-jdk" (version 1.5.0_13) and made it my default Java with:

$ sudo apt-get install sun-java5-jdk
$ sudo update-alternatives --config java

and then it worked.  Now I enter the command and get the "Airport Base Station Configurator" Java application window.

---

