---
title: "SmartSVN Java incompatibility"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by elexhobby on 2010-09-16
I downloaded SmartSVN from the website, and when I try running the smartsvn.sh file, I get the following error:

> Disabling SSE42Intrinsics to work-around bug 6875866.
An incompatible Java version has been detected which has been reported to cause strange bugs. Aborting now. To force SmartSVN to use this Java version, set the VM property smartsvn.checkIncompatibleJava to false (use at your own risk).

Please install the latest release of the SUN Java SE Runtime Environment (JRE) from:
  [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)
or if it is already installed, make sure it is used.

I get the same error on two computers - one running Lucid, the other running Hardy. Both of them have the latest version of Java installed. Could somebody give me insight into what's wrong?

Thanks a lot!

---

### Post by Paddy Landau on 2010-09-19
Which version of Java do you have installed? The one from Sun, or the one that comes default with Ubuntu?

Ubuntu's default for 10.04 is OpenJDK and Icedtea, not Sun (I don't remember Hardy's default).

Check with Ubuntu Software Centre (or with Synaptic Package Manager). Try uninstalling OpenJDK and Icedtea, and installing Sun's Java (you may have to install Ubuntu restricted extras first).

That may help.

---

### Post by jtarin on 2010-09-19
Determine the version your application calls for download if necessary then:
[URL="https://help.ubuntu.com/community/Java#Choosing the default Java to use"]change the default Java pointed to by /usr/bin/java. You must explicitly set this:
[/URL]

---

