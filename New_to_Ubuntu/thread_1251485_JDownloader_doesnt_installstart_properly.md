---
title: "JDownloader doesnt install/start properly"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by ovie on 2009-08-27
i just tried installing jdownloader, but had issues:

-------
MY system/software info
i'm running ubuntu/64, and running this version of java

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)
-------

when i try to run:             ./jd.sh
it opens the jdownloader GUI which loads for a bit (the very 1st time, i think it updated the jdownloader software), and then shuts down randomly while the program is still loading.  it always shuts down while loading the language (the language light on the 'loading menu' is always the only one lit up).

this is what shows on the terminal when i run "./jd.sh", after the jdownloader GUI opens and then shuts down unexpectedly, the terminal gets stuck at the last line of the 'code' below

```

JD Installation found: Starting JD now
00s.057 - INFO [jd.Main(main)] -> Start JDownloader
JAR
00s.870 - FINEST [jd.utils.JDUtilities(getJDClassLoader)] -> Create Classloader: for: /root/.jd
00s.936 - FINEST [jd.JDClassLoader(<init>)] -> rootDir:/root/.jd
/root/.jd
 file:/root/.jd/jd
01s.146 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDWebinterface.jar
01s.250 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDChat.jar
01s.355 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDFolderWatch.jar
01s.430 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/schedule.jar
01s.474 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDRemoteControl.jar
01s.537 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDHJMerge.jar
01s.646 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDShutdown.jar
01s.753 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDGrowl.jar
01s.877 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDInfoFileWriter.jar
01s.973 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDHTTPLiveHeaderScripter.jar
02s.089 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDUnrar.jar
02s.289 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDLangFileEditor.jar
02s.459 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDTray.jar
02s.517 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/plugins/JDExternInterface.jar
03s.115 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /root/.jd/JDownloader.jar
03s.146 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaBlackMoon.jar
03s.262 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaWhiteVision.jar
03s.288 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/synthetica.jar
03s.315 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaOrangeMetallic.jar
03s.359 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaBatik.jar
03s.361 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaSkyMetallic.jar
03s.371 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaBlueMoon.jar
03s.390 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaSilverMoon.jar
03s.393 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaMauveMetallic.jar
03s.418 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaSimple2D.jar
03s.421 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaBlackStar.jar
03s.424 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaBlueIce.jar
03s.427 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /root/.jd/libs/laf/syntheticaBlueSteel.jar
04s.519 - FINER [jd.config.DatabaseConnector(<init>)] -> Loading database
04s.614 - FINER [jd.config.DatabaseConnector(checkDatabaseHeader)] -> Checking database
06s.187 - INFO [jd.Main(main)] -> init Splash
08s.533 - INFO [jd.gui.swing.laf.LookAndFeelController(setUIManager)] -> Use Look & Feel: de.javasoft.plaf.synthetica.SyntheticaSimple2DLookAndFeel
17s.214 - INFO [jd.Main(main)] -> init Eventmanager
Loaded language: English
17s.249 - INFO [jd.utils.locale.JDL(parseLanguageFile)] -> parse lng file /root/.jd/jd/languages/en.loc
18s.170 - INFO [jd.utils.locale.JDL(parseLanguageFile)] -> parse lng file end /root/.jd/jd/languages/en.loc
18s.197 - INFO [jd.Main(main)] -> init Localisation
18s.906 - INFO [jd.Main(go)] -> Thu Aug 27 17:39:17 EDT 2009
18s.907 - INFO [jd.Main(go)] -> init Configuration
jd.http.Browser$BrowserException: connect timed out
    at jd.http.Browser.loadConnection(Browser.java:1011)
    at jd.http.Browser.getPage(Browser.java:336)
    at jd.utils.locale.JDL.getCountryCodeByIP(Unknown Source)
    at jd.Installer.<init>(Unknown Source)
    at jd.JDInit.loadConfiguration(Unknown Source)
    at jd.Main.go(Unknown Source)
    at jd.Main.access$0(Unknown Source)
    at jd.Main$3.run(Unknown Source)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
    at jd.Installer.<init>(Unknown Source)
    at jd.JDInit.loadConfiguration(Unknown Source)
    at jd.Main.go(Unknown Source)
    at jd.Main.access$0(Unknown Source)
    at jd.Main$3.run(Unknown Source)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)


```pls help:
what can i do to get jdownloader working?

---

### Post by ovie on 2009-08-27
ps.
i downloaded it using the steps here:

[http://www.ubuntu-inside.me/2009/02/jdownloader-ultimate-freepremium.html](http://www.ubuntu-inside.me/2009/02/jdownloader-ultimate-freepremium.html)

and if i try to use another terminal window to open/install jdownloader, i get this message:

01s.401 - INFO [jd.Main(main)] -> existing jD instance found!
01s.448 - INFO [jd.Main(main)] -> There is already a running jD instance

---

### Post by binbash on 2009-08-27
Hey ovie,

I am the poster of that article. That warning means there is already a Jdownloader process is running. I checked your output and i saw that you have installed Jdownloader to your root folder : 

/root/.jd/plugins/

Reboot your box, follow the steps at the article and install it to your USER account.

Be sure you are following these steps as NORMAL USER :

```
Ok, now let's download Jdownloader, download it via :

$wget -c [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh)

After download let's make it executable and run it :

$chmod +x jd.sh
$./jd.sh
```

Optional :

You may want to remove your /root/.jd folder since you installed it under root account.

Feel free to send me a PM or send a comment to that blog post if you want a fast answer.

---

