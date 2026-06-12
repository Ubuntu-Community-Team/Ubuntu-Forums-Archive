---
title: "Upgraded and now Java will not work"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-08
Hi,

I "upgraded" from 8.10 to 9.10 and now I can't get Java to work.

When I type **Which Java** it tells me the folder it's installed in

/usr/bin/java

**and java version....**

java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.2) (6b18-1.8.2-4ubuntu1~9.10.1)
OpenJDK Server VM (build 16.0-b13, mixed mode)

But when I go to any Java Test site, they all report Java is not working.

I guess it's a browser issue?

FireFox 3.6.12


Any suggestions?

thx!

---

### Post by blazemore on 2010-11-08
Try this:
```
sudo update-java-alternatives -s java-6-openjdk
```

---

### Post by mistypotato on 2010-11-08
> **blazemore said:**
> Try this:
```
sudo update-java-alternatives -s java-6-openjdk
```


error: no alternatives for xulrunner-1.9-javaplugin.so.

---

### Post by mistypotato on 2010-11-08
[SIZE="4"][COLOR="DarkRed"]I just DISABLED Ubuntu Firefox Modifications plugin and Voila ![/COLOR][/SIZE]

Java now works

---

### Post by ajgreeny on 2010-11-08
I disabled the ubuntu firefox modifications add-on some time ago, probably when using 9.10, as it was causing a lot of other add-ons and plugins to not work, including googlebar-lite, which I find invaluable.

I have even uninstalled ubufox (this is the package name) from synaptic as well now, as I never used it, even when I had it.

---

