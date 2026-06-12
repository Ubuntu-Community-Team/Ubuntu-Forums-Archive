---
title: "Sun Java 6 web start"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by bob brazie on 2009-07-25
Ubuntu 9.04

I have installed an application that uses Sun Java Web start to, well, run.

I can right click the file that opens the application and choose “open with sun java 6 web start” but the application only gives me an error message saying “failed to open the application.

I guess my question is how do I verify that Sun Java 6 Web Start is installed and working on y system.

Thanks in advance. Bob.

---

### Post by TigerCR1200 on 2009-07-25
The first thing to try would be to list of installed java.
```
dpkg -l | grep jre
```

It should give you and output like this:
```
tiger@frankenstein:~$ dpkg -l | grep jre
ii  icedtea-6-jre-cacao                        6b16~pre4-0ubuntu7                       Alternatve JVM for OpenJDK, using Cacao
ii  openjdk-6-jre                              6b16~pre4-0ubuntu7                       OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless                     6b16~pre4-0ubuntu7                       OpenJDK Java runtime, using Hotspot JIT (hea
ii  openjdk-6-jre-lib                          6b16~pre4-0ubuntu7                       OpenJDK Java runtime (architecture independe

```

---

### Post by bob brazie on 2009-07-25
bob@bob-laptop:~$ dpkg -l | grep jre
ii  sun-java6-jre                              6-14-0ubuntu1.9.04                        Sun Java(TM) Runtime Environment (JRE) 6 (ar
bob@bob-laptop:~$ 

This is my output. I did notice that in Mozilla Firefox in the edit/preferances/applications that jave web start application is listed.

---

### Post by mocoloco on 2009-07-25
TigerCR1200 is using the OpenJDK release of Java.  If you happen to have Sun's Java (like I do), your output might look like this:
```
ii  sun-java6-jre                              6-14-0ubuntu1.9.04                        Sun Java(TM) Runtime Environment (JRE) 6 (ar

```

Also I have a launcher called "Sun Java 6 Web Start" under Applications -> Internet.  It executes a file that links to /usr/bin/javaws.  So do 
```
which javaws
```
and post that output along with what TigerCRI200 listed.

---

### Post by mocoloco on 2009-07-25
Looks like we posted at the same time :P
So you've got Sun's jre.  So from a terminal do
```
/usr/bin/javaws /path/to/your/app/name_of_your_app
```
And see if it provides more info on why it's failing.

---

### Post by bob brazie on 2009-07-25
I too have that icon in applications/internet but when I click on it nothing happens.

---

### Post by bob brazie on 2009-07-25
When I run the command: /usr/bin/javaws /path/to/your/app/name_of_your_app I get a pop up style error saying &#8220;unable to launch the application&#8221;

It comes with details in two tabs but I can't copy/paste them. 

Maybe this? Could not load file/URL specified: /path/to/your/app/name_of_your_app

---

### Post by TigerCR1200 on 2009-07-26
/usr/bin/javaws /path/to/your/app/name_of_your_app when you run this command you need to change the part that says /path/to/your/app/name_of_your_app. It would probably resemble something like /home/bob/app.jar

---

### Post by bob brazie on 2009-07-26
I thought as much but i am not sure where this is located so i can change the path.

Also how do i know that Web Start is installed and is installed correctly?

---

### Post by satdat on 2009-07-27
i am getting  this error message
Java Plug-in 1.6.0_14
Using JRE version 1.6.0_14-b08 Java HotSpot(TM) Client VM
User home directory = /home/sujay
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------


Reading certificates from 11 [http://charting.bseindia.com/charting/equis/metastock/ms4javav2.jar](http://charting.bseindia.com/charting/equis/metastock/ms4javav2.jar) | /home/sujay/.java/deployment/cache/6.0/53/20ef9b75-2537c8fc.idx
BColor : e6eef1, FColor : 0089CF
MetaStock Online
Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
Version 2.5.4
Mar 27 2000 12:00 MST
MS4Java --> Feature level at version 2.0.0
MS4Java --> In CheckClientKey()
MS4Java --> This client key (#8FB-700-0631) will expire on 3/2010.
MS4Java --> Client key (8FB-700-0631) is valid
MS4Java --> Language URL: 'http://charting.bseindia.com/charting/equis/metastock/english.lang'
MS4Java --> Parameters:
MS4Java -->   AdsURL                 = [http://charting.bseindia.com/charting/equis/metastock/ads](http://charting.bseindia.com/charting/equis/metastock/ads)
MS4Java -->   Applet Name Font Size  = 12
MS4Java -->   Applet Name Position   = west
MS4Java -->   AutoPriceStyleChanges  = true
MS4Java -->   Copyright notice       = Copyright (C) 1997-2000 Equis International, Inc.
All Rights Reserved.
MS4Java -->   DateFormat             = MM/DD/YY
MS4Java -->   EODDataURL             = [http://charting.bseindia.com/charting/history.asp](http://charting.bseindia.com/charting/history.asp)
MS4Java -->   ForceUpperParam        = true
MS4Java -->   HelpURL                = [http://charting.bseindia.com/charting/help/index.asp](http://charting.bseindia.com/charting/help/index.asp)
MS4Java -->   HumanLanguage          = ENGLISH
MS4Java -->   IntradayDataURL        = [http://charting.bseindia.com/charting/intraday.asp](http://charting.bseindia.com/charting/intraday.asp)
MS4Java -->   MS4JVersion            = 2.0.0
MS4Java -->   NewsURL                = [http://www.bseindia.com/charting/news.asp?SYMBOL=](http://www.bseindia.com/charting/news.asp?SYMBOL=)
MS4Java -->   RelativeStrengthSymbol = BSE303
MS4Java -->   Removed Indicators     = NONE
MS4Java -->   SearchDialogHeight     = 0
MS4Java -->   SetDefaultIndicator    = Moving Average (value1=15, value2=15)
MS4Java -->   ShowAdPanel            = false
MS4Java -->   ShowData               = true
MS4Java -->   ShowDataErrorMessages  = true
MS4Java -->   ShowDebugMessages      = true
MS4Java -->   ShowDocumentHelpFrame  = _self
MS4Java -->   ShowDocumentNewsFrame  = _new
MS4Java -->   ShowHelpButton         = true
MS4Java -->   ShowIntradayVolume     = true
MS4Java -->   ShowNewsButton         = true
MS4Java -->   ShowPeriodicityControl = false
MS4Java -->   ShowPriceStyleControl  = false
MS4Java -->   ShowSymbolControl      = false
MS4Java -->   YAxisWidth             = 50
java.lang.NullPointerException
	at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])
	at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:113)
	at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
	at java.awt.Component.setBackground(Component.java:1720)
	at equis.metastock.MS4Java.init([DashoPro-V1.2-120198])
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1528)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
Exception in thread "Thread-10" java.lang.NullPointerException
	at equis.metastock.MS4Java.run([DashoPro-V1.2-120198])
	at java.lang.Thread.run(Thread.java:619)
[http://charting.bseindia.com/charting/indices.asp](http://charting.bseindia.com/charting/indices.asp)
url =http://charting.bseindia.com/charting/G_sec_choice.asp
java.io.IOException: Server returned HTTP response code: 500 for URL: [http://charting.bseindia.com/charting/G_sec_choice.asp](http://charting.bseindia.com/charting/G_sec_choice.asp)
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1305](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1305))
	at java.net.URL.openStream(URL.java:1009)
	at equis.metastock.TestMS4Java.G_sec_choices(TestMS4Java.java:957)
	at equis.metastock.TestMS4Java.init(TestMS4Java.java:1179)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1528)
	at java.lang.Thread.run(Thread.java:619)
pls help
thx in advance

---

