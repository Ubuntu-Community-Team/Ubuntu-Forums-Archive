---
title: "Wurm Online (JavaWS Application) Fails to start"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Zopiac on 2009-01-24
Wurm online is a java based web game that you can download the .jnlp file of to start it right from your desktop. However, it doesnt load properly. It gets to the 'downloading updates' window, but then it crashes. This is the terminal output:

```
zopiac@zopiac-desktop:~$ javaws /home/zopiac/wurmclient.jnlp 
java.lang.NullPointerException
	at net.sourceforge.jnlp.tools.JarSigner.verifyJars(JarSigner.java:192)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.verifyJars(JNLPClassLoader.java:609)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:302)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:134)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:191)
	at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:509)
	at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:334)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:600)
netx: Initialization Error: Could not initialize applet. (net.sourceforge.jnlp.LaunchException Fatal: Initialization Error: A fatal error occurred while trying to verify jars.)
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: Could not initialize applet.
	at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:519)
	at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:334)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:600)
Caused by: net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:308)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:134)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:191)
	at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:509)
	... 2 more
Caused by: 
net.sourceforge.jnlp.LaunchException: Fatal: Initialization Error: A fatal error occurred while trying to verify jars.
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.initializeResources(JNLPClassLoader.java:308)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.<init>(JNLPClassLoader.java:134)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.getInstance(JNLPClassLoader.java:191)
	at net.sourceforge.jnlp.Launcher.createApplication(Launcher.java:509)
	at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:334)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:600)
zopiac@zopiac-desktop:~$ 

```

just installed hava 6 from synaptics not too long ago. I have played this game on Ubuntu before, but it had always worked, so im not sure what caused this (this is, however, the first time ive tried to play this on this installation of the game)

---

### Post by txcrackers on 2009-01-24
You'll need to talk to the WURMS folks - this is not a Java problem. The "NullPointerException" usually means something's not programmed/configured correctly.

---

### Post by ubu_dynamite on 2009-01-26
I use this client on ubuntu hardy
[http://www.wurmonline.com/client/wurmclient_netx.jnlp](http://www.wurmonline.com/client/wurmclient_netx.jnlp)
found here
[http://www.wurmonline.com/forum/index.php?topic=10801.0](http://www.wurmonline.com/forum/index.php?topic=10801.0)

---

### Post by jtayl22 on 2009-06-18
I solved a similar problem on a Linux amd64 (aka x64) box by installing jdk1.6.0_14 from Sun. java-6-sun-1.6.0.07, which is the current version in the Ubuntu 8.04 disto does not include javaws. You need j6u12 or greater.

---

### Post by jtayl22 on 2009-07-12
[LIST]
[*]32-bit Linux is easy but the 64-bit distros have an issue
[*]I solved the Java Web Start problem on a Linux amd64 (aka x64) box by installing jdk1.6.0_14 from Sun.
[*]java-6-sun-1.6.0.07, which is the current version in the Ubuntu 8.04 disto does not include javaws.
[*]You need j6u12 or greater.
[*]You can run "sudo update-alternatives --config java" to see which Java releases are installed. I had two:
[INDENT][*]/usr/lib/jvm/java-6-sun/jre/bin/java
[*]/usr/lib/jvm/java-6-openjdk/jre/bin/java[/INDENT]
[*]You need to have the alternative set to the Sun JVM (not OpenJDK)
[*]"/usr/lib/jvm/java-6-sun/jre/bin/java -version" should report 1.6.0_12 or greater
[/LIST]

---

