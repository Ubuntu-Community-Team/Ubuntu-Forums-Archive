---
title: "looking at how to install open laszlo please"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by kapi on 2009-06-23
Downloaded the tar file but am unsure what to do next

any help is much appreciated

Thanks

---

### Post by zvacet on 2009-06-24
Did you tried to follow [install-instructions?]("http://www.openlaszlo.org/lps3/docs/installation/install-instructions.html")

---

### Post by IAmCorbin on 2009-08-20
I am attempting to get OpenLaszlo setup and having a very difficult time, could someone help please?

I am running Ubuntu 8.10 and I am stuck on the $JAVA_HOME var:

```

corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24$ echo $JAVA_HOME

corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24$ which java
/usr/bin/java
corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24$ export JAVA_HOME='/usr/bin/java'
corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24$ cd bin
corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24/bin$ sh startup.sh
The JAVA_HOME environment variable is not defined correctly
This environment variable is needed to run this program
NB: JAVA_HOME should point to a JDK not a JRE
corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24/bin$ echo $JAVA_HOME
/usr/bin/java
corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24/bin$ export JAVA_HOME='/usr/lib/jvm/java-6-openjdk/'
corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24/bin$ sh startup.sh
The JAVA_HOME environment variable is not defined correctly
This environment variable is needed to run this program
NB: JAVA_HOME should point to a JDK not a JRE
corbin@Punisher:/usr/local/lps-4.5.1/Server/tomcat-5.0.24/bin$ echo $JAVA_HOME
/usr/lib/jvm/java-6-openjdk/

```

I have been googling by eyes out and can't seem to figure this out

---

