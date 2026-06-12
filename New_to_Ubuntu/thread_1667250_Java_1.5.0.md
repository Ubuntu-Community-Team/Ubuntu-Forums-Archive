---
title: "Java 1.5.0"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by musendrophilus on 2011-01-14
I want to run an app that requires Java 1.5.0, according to the Ubuntu Software Center I have OpenJDK Java 6 Runtime and Webstart. How are these any different than Java 1.5.0?

To get functionality will I have to remove the current Java 6 and reinstall for a more up to date version?

---

### Post by I8NY on 2011-01-15
Right now you have OpenJDK which is a little different than the real version of java.  The real version is 6.22.  To get it you must first uninstall openJDK then go to the package manager and search for "sun-java"  Install "sun-java6-bin," "sun-java6-jre," "sun-java6-plugin."  It should work now. ;)

---

