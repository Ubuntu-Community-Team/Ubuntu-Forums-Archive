---
title: "How to properly set X11 DISPLAY variable"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by pepperoo on 2011-04-19
I am working with PushToTest and Hudson integration on Ubuntu 'til I got this error:


Started by user anonymous
[workspace] $ /bin/sh -xe /tmp/hudson1471460275085672483.sh
+ /usr/local/PushToTest_TestMaker/TestMaker.sh -t /home/einstein/Documents/attache_files/TestScenarios/Attache.scenario -log-junit var/lib/hudson/jobs/TestAttache/junitreport.xml
Exception in thread "main" java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
	at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
	at java.awt.Window.<init>(Window.java:437)
	at java.awt.Frame.<init>(Frame.java:419)
	at java.awt.Frame.<init>(Frame.java:384)
	at javax.swing.JFrame.<init>(JFrame.java:174)
	at com.pushtotest.tm.console.gui.SplashScreen.<init>(SplashScreen.java:82)
	at com.pushtotest.tm.console.Main.main(Main.java:65)
Finished: FAILURE


So I set DISPLAY variable using terminal:

export DISPLAY=:0.0

I then re-started the build and got this error:



[workspace] $ /bin/sh -xe /tmp/hudson6662897764509587544.sh
+ /usr/local/PushToTest_TestMaker/TestMaker.sh -t /home/einstein/Documents/attache_files/TestScenarios/Attache.scenario -log-junit var/lib/hudson/jobs/TestAttache/junitreport.xml
Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
	at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
	at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:62)
	at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:166)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:142)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:186)
	at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:82)
	at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:111)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:186)
	at java.awt.Toolkit$2.run(Toolkit.java:849)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:841)
	at com.pushtotest.tm.console.gui.SplashScreen.<clinit>(SplashScreen.java:78)
	at com.pushtotest.tm.console.Main.main(Main.java:65)
Finished: FAILURE


As I read through other forums, I ran through someone who solved this by 

select all
export DISPLAY=:0.0

I did this and got:

bash: syntax error near unexpected token 'export'

How do I know which value to use? 

Any thoughts on how to solve my problem? Thanks!

---

### Post by jtarin on 2011-04-19
You could, for example, say:

```
DISPLAY=:0.0 xterm &
```

to just start an X terminal with DISPLAY set; any commands run on that terminal emulator would then have the DISPLAY variable available. In that case, the DISPLAY would be blank.

---

