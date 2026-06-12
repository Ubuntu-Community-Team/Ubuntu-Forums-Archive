---
title: "JAVA_HOME problem"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by BioVirtual on 2010-01-07
**JAVA_HOME problem**             
                                                                Well it's a bit confusing, I downloaded Java from [www.java.com]("http://www.java.com/") and installed it successfully. But when I go to java.com and click on verify Java, it's telling me:

[B]     Quote:
                                                  Oops! You don't have the recommended Java installed.                                 
[/B]     Quote:
                                                 
                                     **Your Java version is 1.6.0_0.** Please click the button below to get the recommended Java for your computer.                                 
and what is the recommended java? **Version 6 Update 17 ! **the one that i just installed.

Anyhow, I tried to configure JAVA_HOME and the result of 
     Code:
      echo $JAVA_HOME 
 is :
     Code:
      /usr/lib/jvm/java-6-openjdk 
when I try to install OpenLaszlo I get:

     Quote:
                                                 The JAVA_HOME environment variable is not defined
This environment variable is needed to run this program                                 

                                                                                                [URL="http://ubuntuforums.org/newreply.php?do=newreply&p=8615179"]
[/URL]

---

### Post by tom.swartz07 on 2010-01-07
I would suggest removing everything related to Java and using this.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
Theres a guide for 32 and 64 bit OS's


This got me set up and running in 3 minutes!

Let me know if you have any problems!

---

### Post by BioVirtual on 2010-01-09
Thanks a lot. The document was excellent. But I still have problem with JAVA_HOME. I verified java installation successfully and run:

 export JAVA_HOME=/opt/java/32/jre1.6.0_17

which is the location of java installation I did according to the document. But I'm still getting the error when I'm trying to install my software (OpenLaszlo):

The JAVA_HOME environment variable is not defined
This environment variable is needed to run this program

Any Idea?

---

### Post by smokinblues on 2010-02-17
I'm running Jaunty, and this is how I installed OpenLazslo.

1. sudo apt-get install sun-java6-jdk
2. sudo update-java-alternatives -s java-6-sun
3. sudo su -
4. export JAVA_HOME=/usr/lib/jvm/java-6-sun/
5. cd /usr/local
6. wget [http://download.openlaszlo.org/4.7.1/openlaszlo-4.7.1-unix.tar.gz](http://download.openlaszlo.org/4.7.1/openlaszlo-4.7.1-unix.tar.gz)
7. tar xvzf openlaszlo-4.7.1-unix.tar.gz
8. /usr/local/lps-4.7.0/Server/tomcat-5.0.24/bin/startup.sh

you should get :
Using CATALINA_BASE:   /usr/local/lps-4.7.0/Server/tomcat-5.0.24
Using CATALINA_HOME:   /usr/local/lps-4.7.0/Server/tomcat-5.0.24
Using CATALINA_TMPDIR: /usr/local/lps-4.7.0/Server/tomcat-5.0.24/temp
Using JAVA_HOME:       /usr/lib/jvm/java-6-sun/

I hope that helps. The key to the JAVA_HOME problem for me was the "sudo update-java-alternatives -s java-6-sun" line.

---

