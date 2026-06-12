---
title: "Problem of Starting JBOSS and setting of JAVA_HOME in Ubuntu 9.04"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by rsg75 on 2009-10-21
I wish to install NewGenlib (an open Source ILMS software) in Ubuntu 9.04. For this purpose, I have to install **jboss-3.2.1_tomcat-4.1.24** in /usr directory and **jdk1.6.0_16** in /usr/local directory.
 

 The following steps have been followed-
 
[LIST=1]
[*]I have unzipped      **jboss-3.2.1_tomcat-4.1.24** in /usr directory
[*]Downloaded **jdk-6u16-linux-i586.bin**
[*]Copied it     into /usr/local directory
[*]Execute     permissions have been set
[LIST=1]
[*]i.e, chmod +x          **jdk-6u16-linux-i586.bin**
[/LIST]
 
[*]Run the     binary file
[LIST=1]
[*]i.e sudo ./         jdk-6u16-linux-i586.bin
[/LIST]
 
[*]Setting     JAVA_HOME
[/LIST]
 for this purpose I edited /etc/profile file as  
 

          export JAVA_HOME=/usr/local/jdk1.6.0_16
          export PATH=$PATH:$JAVA_HOME/bin:$JAVA_HOME/jre/lib: $JAVA_HOME/ jre/javaws  
      export CLASSPATH=$CLASSPATH:"/usr/local/jdk1.6.0_16/lib"  
 

     # JAVA_HOME=/usr/local/jdk1.6.0_16
     # export JAVA_HOME  
 

 But when I start JBOSS Server by following command  
 

 /usr/ jboss-3.2.1_tomcat-4.1.24/bin/./run.sh
 

 It is showing the following  eroor
 ================================================================================ 
 

   JBoss Bootstrap Environment  
 

   JBOSS_HOME: /usr/jboss-3.2.1_tomcat-4.1.24  
 

   JAVA: /usr/local/jdk1.6.0_16/bin/java  
 

   JAVA_OPTS: -server -Dprogram.name=run.sh  
 

   CLASSPATH: /usr/jboss-3.2.1_tomcat-4.1.24/bin/run.jar:/usr/local/jdk1.6.0_16/lib/tools.jar 
 

 ================================================================================ 
 

 16:59:10,052 INFO  [Server] Starting JBoss (MX MicroKernel)...  
 16:59:10,089 INFO  [Server] Release ID: JBoss [WonderLand] 3.2.1 (build: CVSTag=JBoss_3_2_1 date=200305041533)  
 16:59:10,090 INFO  [Server] Home Dir: /usr/jboss-3.2.1_tomcat-4.1.24  
 16:59:10,090 INFO  [Server] Home URL: file:/usr/jboss-3.2.1_tomcat-4.1.24/  
 16:59:10,090 INFO  [Server] Library URL: file:/usr/jboss-3.2.1_tomcat-4.1.24/lib/  
 16:59:10,091 INFO  [Server] Patch URL: null  
 16:59:10,091 INFO  [Server] Server Name: default  
 16:59:10,091 INFO  [Server] Server Home Dir: /usr/jboss-3.2.1_tomcat-4.1.24/server/default  
 16:59:10,092 INFO  [Server] Server Home URL: file:/usr/jboss-3.2.1_tomcat-4.1.24/server/default/  
 16:59:10,092 INFO  [Server] Server Data Dir: /usr/jboss-3.2.1_tomcat-4.1.24/server/default/data  
 16:59:10,092 INFO  [Server] Server Temp Dir: /usr/jboss-3.2.1_tomcat-4.1.24/server/default/tmp  
 16:59:10,092 INFO  [Server] Server Config URL: file:/usr/jboss-3.2.1_tomcat-4.1.24/server/default/conf/  
 16:59:10,093 INFO  [Server] Server Library URL: file:/usr/jboss-3.2.1_tomcat-4.1.24/server/default/lib/  
 16:59:10,093 INFO  [Server] Root Deployemnt Filename: jboss-service.xml  
 16:59:10,096 INFO  [Server] Starting General Purpose Architecture (GPA)...  
 1**6:59:10,214 ERROR [Server] Failed to start  **
 javax.management.InstanceNotFoundException: JMImplementation:service=LoaderRepository,name=Default  
     at com.sun.jmx.interceptor.DefaultMBeanServerInterceptor.getMBean(DefaultMBeanServerInterceptor.java:1094) 
     at com.sun.jmx.interceptor.DefaultMBeanServerInterceptor.invoke(DefaultMBeanServerInterceptor.java:833) 
     at com.sun.jmx.mbeanserver.JmxMBeanServer.invoke(JmxMBeanServer.java:761) 
     at org.jboss.system.server.ServerImpl.initBootLibraries(ServerImpl.java:480) 
     at org.jboss.system.server.ServerImpl.doStart(ServerImpl.java:316)  
     at org.jboss.system.server.ServerImpl.start(ServerImpl.java:272)  
     at org.jboss.Main.boot(Main.java:150)  
     at org.jboss.Main$1.run(Main.java:388)  
     at java.lang.Thread.run(Thread.java:619)  
 **Failed to boot JBoss:  **
 javax.management.InstanceNotFoundException: JMImplementation:service=LoaderRepository,name=Default  
     at com.sun.jmx.interceptor.DefaultMBeanServerInterceptor.getMBean(DefaultMBeanServerInterceptor.java:1094) 
     at com.sun.jmx.interceptor.DefaultMBeanServerInterceptor.invoke(DefaultMBeanServerInterceptor.java:833) 
     at com.sun.jmx.mbeanserver.JmxMBeanServer.invoke(JmxMBeanServer.java:761) 
     at org.jboss.system.server.ServerImpl.initBootLibraries(ServerImpl.java:480) 
     at org.jboss.system.server.ServerImpl.doStart(ServerImpl.java:316)  
     at org.jboss.system.server.ServerImpl.start(ServerImpl.java:272)  
     at org.jboss.Main.boot(Main.java:150)  
     at org.jboss.Main$1.run(Main.java:388)  
     at java.lang.Thread.run(Thread.java:619)
 
[B]
 I have also tried it by editing the/etc/bash.bashrc, but it showed also  same results.[/B]
 **To find my JAVA_HOME** using the locate command for a file belonging to the JDK.
 [B]locate /rt.jar
[/B]The following results appeared
/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/rt.jar 
/usr/local/jdk1.6.0_16/jre/lib/rt.jar 
/usr/local/jre1.6.0_16/lib/rt.jar 
Kindly Help me

---

### Post by elvisd on 2009-10-21
Hi.
I think that jboss 3.2 can't run on jdk 1.6!
Try with a jdk 1.5

hth

---

