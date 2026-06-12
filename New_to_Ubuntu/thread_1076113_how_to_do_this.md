---
title: "how to do this???"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by mash.ky on 2009-02-21
i'm using ubuntu 8.10. i need to install
>> java 1.5
>> netbeans 6.0
>> tomcat 5
>> apache 2
>> mysql
>> php 5

i tried to install above packages in to my machine but finally ended up with a huge mess. i did this several times but no success. can anyone pls help me on this. it would be very helpful if somebody explain in detail.

ps: i hav tried so many documents. most of them are writeen for different different versions. pls help me!!! i need only those versions which i mensioned above.

---

### Post by Mercury_Alpha on 2009-02-21
If you need older versions of those packages, you can go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"), select Hardy (or older if you need it), and search for your package. On the results page, click on the name of the Ubuntu release to go to a profile page for that package. There's another link at the bottom of the page that will take you to the actual download page.

---

### Post by chmbrs on 2009-02-21
did you try to install them in the package manager?

do an update?

---

### Post by konqueror7 on 2009-02-21
with java and netbeans, i believe there is a bundled version of it in sun's web site...

as for tomcat, you can install it inside netbeans if you want...

as for mysql, php, and apache2, they are all in the repositories...here's a [guide]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by mash.ky on 2009-02-21
actually tomacat can be installed with netbaens ide but the thing is by default it installs tomcat 6 and java 6. but i need java 5 and tomcat 5. dat's da main issue.

---

### Post by mash.ky on 2009-02-21
yes i tied the package manager to install as well as tried installing in termina.

---

### Post by konqueror7 on 2009-02-21
[here's ]("http://java.sun.com/j2se/1.5.0/download-netbeans.html") a bundled java 5,,,usually netbeans in linux, does only contain basic components, as compared to the windows installer...

also about tomcat, here's the [ubuntu documentation]("https://help.ubuntu.com/community/ApacheTomcat5")

the php-apache2-mysql guide above, have you tried it? worked for me...

---

### Post by mash.ky on 2009-02-21
thanx for the link. i  install jdk and jre 1.5. and i hav installed netbeans 6.0 successfully using netbeans-6.0-linux.sh. but it is not displayed in the application menu or the synaptic manager. in synaptic it only shows the netbeans 6.1 version which is not installed. what shall i do?

---

### Post by konqueror7 on 2009-02-21
haven't tried installing netbeans 6.0...just create a new menu shortcut with the command
```
/bin/sh "/usr/local/netbeans-6.5/bin/netbeans"
```

just change the directory of netbeans depending if you installed it on a different path...

also why use netbeans 6.0? because 6.5 in my opinion is better and faster, and has many other improvements since 6.0...

---

### Post by mash.ky on 2009-02-23
ok can u remember the link u gave me to download jdk-1_5_0_17-nb-6_5-linux-ml.sh.... this consist jdk-1_5_0_17. but i hav already installed sun java5-bin, sun java5-jre, sun java5-demo, sun java5-jdk 1_5_0_16. is it ok to install jdk-1_5_0_17-nb-6_5-linux-ml.sh without uninstalling the previous java files?

---

### Post by konqueror7 on 2009-02-23
you don't really need to uninstall it, it installs in different folder depending on the version...

also, with the jdk/netbeans bundle installer, it allows you to specify which location to install both applications...

---

### Post by mash.ky on 2009-02-23
hey thanx dude. i got everything clear. i installed netbeans 6.5 and jdk1.5.0_17 into my home folder and then replaced the previous java version with jdk1.5.0_17 @ /usr/lib/jvm. i renamed it as java-1.5.0-sun-1.5.0.17. when i type ```
java -version
``` it gives ```
java version "1.5.0_17"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_17-b04)
Java HotSpot(TM) Server VM (build 1.5.0_17-b04, mixed mode)
```

so i think now it's working. but when i installed tomcat 5.5 and run ```
sudo /usr/share/tomcat5.5/bin/startup.sh

```
it gives```
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

```

even i hav added```
#Stuff we added to make tomcat go
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.17/
export CLASSPATH=/usr/share/tomcat5.5/common/lib/jsp-api.jar:/usr/share/tomcat5.5/common/lib/servlet-api.jar
```
to the .bashrc.

pls help me on this last question. hope i'm not becoming a real trouble to you....? thanx again.

---

### Post by konqueror7 on 2009-02-23
have you imported JAVA_HOME to your PATH? did you add these following lines after declaring all your environment variables?
```
export PATH="$PATH:JAVA_HOME/bin"
```

you can also refer [here]("http://www.spaceprogram.com/knowledge/2006/05/installing-java-5-jdk-and-tomcat-on.html")...

---

### Post by mash.ky on 2009-02-23
thanks a lot konqueror.:KS

---

### Post by konqueror7 on 2009-02-23
your welcome...:D

---

