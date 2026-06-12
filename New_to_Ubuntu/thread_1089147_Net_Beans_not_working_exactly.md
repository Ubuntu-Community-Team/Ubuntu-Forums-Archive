---
title: "Net Beans not working exactly"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by sundarrajan on 2009-03-06
Hi

I have installed Net beans 6.5 in Ubuntu and when i try to build the program the building process is not successful. Even though my program is error free or when i use the sample program within the system its showing me error while preverify !

I have copied down the error message as follows:

Preverifying 3 file(s) into /home/sundarrajan/NetBeansProjects/PhotoAlbum1/build/preverified directory.
java.io.IOException: Cannot run program "/home/sundarrajan/netbeans-6.5/mobility8/WTK2.5.2/bin/preverify": java.io.IOException: error=2, No such file or directory
        at java.lang.ProcessBuilder.start(ProcessBuilder.java:459)
        at java.lang.Runtime.exec(Runtime.java:593)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.tools.ant.taskdefs.Execute$Java13CommandLauncher.exec(Execute.java:832)
        at org.apache.tools.ant.taskdefs.Execute.launch(Execute.java:447)
        at org.apache.tools.ant.taskdefs.Execute.execute(Execute.java:461)
        at org.netbeans.mobility.antext.PreverifyTask.execute(PreverifyTask.java:225)
        at org.apache.tools.ant.UnknownElement.execute(UnknownElement.java:288)
        at sun.reflect.GeneratedMethodAccessor30.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.tools.ant.dispatch.DispatchUtils.execute(DispatchUtils.java:106)
        at org.apache.tools.ant.Task.perform(Task.java:348)
        at org.apache.tools.ant.Target.execute(Target.java:357)
        at org.apache.tools.ant.Target.performTasks(Target.java:385)
        at org.apache.tools.ant.Project.executeSortedTargets(Project.java:1337)
        at org.apache.tools.ant.Project.executeTarget(Project.java:1306)
        at org.apache.tools.ant.helper.DefaultExecutor.executeTargets(DefaultExecutor.java:41)
        at org.apache.tools.ant.Project.executeTargets(Project.java:1189)
        at org.apache.tools.ant.module.bridge.impl.BridgeImpl.run(BridgeImpl.java:273)
        at org.apache.tools.ant.module.run.TargetExecutor.run(TargetExecutor.java:499)
        at org.netbeans.core.execution.RunClassThread.run(RunClassThread.java:151)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
        at java.lang.UNIXProcess.<init>(UNIXProcess.java:148)
        at java.lang.ProcessImpl.start(ProcessImpl.java:65)
        at java.lang.ProcessBuilder.start(ProcessBuilder.java:452)
        ... 24 more
BUILD FAILED (total time: 1 second)

Help me to get rid of this problem and guide me how to work with net beans IDE 6.5 

Note : I have all the additional components required for Ubuntu for example sun-java6-jdk.


Thank you well in advance !!!:o:o:o

---

