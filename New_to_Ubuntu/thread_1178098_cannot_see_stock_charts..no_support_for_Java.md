---
title: "cannot see stock charts..no support for Java?"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by kewl_123 on 2009-06-04
Hi,
      I am using Hardy on my laptop and when I visit some sites to see the charts for shares, I dont get them. I get the message in the window where charts are to be displayed:

The test program would appear here if your browser supported Java.

I am using XP on same laptop and can see charts in XP.
an someone please tell me what I need to do as I want to do my trading using Ubuntu and not XP.
thank you.

---

### Post by neo.patrix on 2009-06-04
If you can send post the links for websites, I can check it out. also which browser are you using on both Windows XP and Ubuntu.

As an try you can check if output for command "java -version" in terminal.

---

### Post by mcduck on 2009-06-04
Java isn't included by default, you need to install it yourself.

[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by kewl_123 on 2009-06-04
Hi,

The site I am visiting is:
 

[http://charting.bseindia.com/charting/index.asp?SYMBOL=500241](http://charting.bseindia.com/charting/index.asp?SYMBOL=500241)

output of the command java -version is:

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>

What package do I need to select?

Also in the link help.ubuntu.com/community/Java

it says:

"To get Sun Java under Ubuntu 7.04 or later running on Intel or PowerPC platform, you should enable the Universe repository in Add/Remove programs, and install either the openjdk-6-jre package or the sun-java6-bin package. (Note: PowerPC version is slow). "

How do I enable Universe Repository?
What is PowerP platform?
Do i go for openjdk or sun-java?

Seems I am asking too many questions...but really need to get my transactions off windows..
Thank you.

---

### Post by neo.patrix on 2009-06-04
Java is not present on your system. OpenJDK or Sun Java are good options. You can check following link for details on Sun Java

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

Also it is possible to install Sun-JRE from Applications->Add/Remove but I am not very sure how it handles configuration details. Within Firefox you can check, Preferences-->Contents, if Java is enabled.

As far as, stocks website is concerned, it is also giving me error. I am sure enough that my options to use Java with Firefox are set properly (OpenJDK). Unforunately website does not give much technical details about which jre it might need. BSE hmm.. Bombay Stock Exchange?

Edit :

You will have to install Sun Java 6 to see that particular WebPage, ideally it 
should be neutral to OpenJDK or SunJava, but well we do not live in perfect world.

I have tried it on Intrepid (Ubuntu 8.10) I hope procedure for your particular installation should be nearly similar.

1) Check if /etc/apt/sources.list has multiverse sources, something like

> deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) intrepid multiverse

If not, you can edit file and save it , in root-user mode. Also update your lists
with command

> sudo apt-get update

2) Install java-6-sun packages

> sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

3) Check the output of java -version, should be something like

> patrix@patrix-laptop:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)


---

### Post by mcduck on 2009-06-04
> **kewl_123 said:**
> Hi,

The site I am visiting is:
 

[http://charting.bseindia.com/charting/index.asp?SYMBOL=500241](http://charting.bseindia.com/charting/index.asp?SYMBOL=500241)

output of the command java -version is:

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>

What package do I need to select?

Also in the link help.ubuntu.com/community/Java

it says:

"To get Sun Java under Ubuntu 7.04 or later running on Intel or PowerPC platform, you should enable the Universe repository in Add/Remove programs, and install either the openjdk-6-jre package or the sun-java6-bin package. (Note: PowerPC version is slow). "

How do I enable Universe Repository?
What is PowerP platform?
Do i go for openjdk or sun-java?

Seems I am asking too many questions...but really need to get my transactions off windows..
Thank you.

To enable Universe, go to System/Administration/Software Sources, and on the "Ubuntu Software"-tab make sure "Community-maintained Open Source software (universe) is enabled.

For maximum compatibility I recommend getting the Sun-Java.

PowerPC is a processor architecture, most commonly found on old Macs and Playstation 3. Unless your computer is one of those you's be using some Intel-compatible architecture instead.

Anyway, the easiest way to get things working is to go to Applications->Add/Remove, make sure it's set to show "All available applications" and then search for "java". Sun java 6 Runtime should be the first of the applications that appear... If you do it this way you don't even need to enable Universe repository separately, instead you'll just get a message asking if you want to enable it.

---

### Post by kewl_123 on 2009-06-05
Hi,
   I first tried to install java with the sudo apt command. Unfortunately, before it could complete I got disconnected and I got the message:

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Then next time I read the post here and tried to do it with add/remove programmes. It worked, and for "java -version" command I get:

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)


Java is enabled in my browser.
However, I am still unable to see the charts on the site

[http://charting.bseindia.com/charting/index.asp?SYMBOL=500241](http://charting.bseindia.com/charting/index.asp?SYMBOL=500241)

Can anyone please tell me whats missing?

Thank you.

---

### Post by satdat on 2009-07-10
i am getting this error after installing java
"Java Plug-in 1.6.0_14
Using JRE version 1.6.0_14-b08 Java HotSpot(TM) Server VM
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
[http://charting.bseindia.com/charting/indices.asp](http://charting.bseindia.com/charting/indices.asp)
java.lang.NullPointerException
	at equis.metastock.MS4Java.repaint([DashoPro-V1.2-120198])
	at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:113)
	at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
	at java.awt.Component.setBackground(Component.java:1720)
	at equis.metastock.MS4Java.init([DashoPro-V1.2-120198])
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1528)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
Exception in thread "Thread-12" java.lang.NullPointerException
	at equis.metastock.MS4Java.run([DashoPro-V1.2-120198])
	at java.lang.Thread.run(Thread.java:619)
url =http://charting.bseindia.com/charting/G_sec_choice.asp
java.io.IOException: Server returned HTTP response code: 500 for URL: [http://charting.bseindia.com/charting/G_sec_choice.asp](http://charting.bseindia.com/charting/G_sec_choice.asp)
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1305](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1305))
	at java.net.URL.openStream(URL.java:1009)
	at equis.metastock.TestMS4Java.G_sec_choices(TestMS4Java.java:957)
	at equis.metastock.TestMS4Java.init(TestMS4Java.java:1179)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1528)
	at java.lang.Thread.run(Thread.java:619)
"
plas guide me how to correct it
thanks
satish

---

