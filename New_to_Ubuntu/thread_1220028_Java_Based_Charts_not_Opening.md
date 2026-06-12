---
title: "Java Based Charts not Opening"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by StOlEnDeStInY on 2009-07-22
This is a problem that I have started facing very recently. I have been using Ubuntu since the last one and a half years without this problem earlier as I use to install Java easily. When I access the site: [http://www.indiabulls.com/securities/research/techanalysis/tech_analysis.aspx](http://www.indiabulls.com/securities/research/techanalysis/tech_analysis.aspx) I get the error,  "MetaStock for Java would appear here if your browser supported Java."

When I type java -version in terminal I get

>  java -version
java version "1.5.0"
gij (GNU libgcj) version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Previous similar posts didn't help :( 

I've a dual bootable system and they use to open with ease in Windows until some stupid virus is blocking my web browsers from browsing any website.

My dad needs to check stock charts and this is an urgent problem.. Thanks in advance! :)

---

### Post by redsoxreed on 2009-07-22
I highly doubt a virus is stopping you from browsing web sites.  Even if it is windows.  If you're using Firefox, this might help:

[http://support.mozilla.com/en-US/kb/Using+the+Java+plugin+with+Firefox](http://support.mozilla.com/en-US/kb/Using+the+Java+plugin+with+Firefox) (these instructions apply to linux and windows)

---

### Post by satdat on 2009-07-27
i am getting this error when i try to see charts on bse
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
thanks in advance

---

### Post by StOlEnDeStInY on 2009-07-27
> **satdat said:**
> i am getting this error when i try to see charts on bse
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
    at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1305]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1305"))
    at java.net.URL.openStream(URL.java:1009)
    at equis.metastock.TestMS4Java.G_sec_choices(TestMS4Java.java:957)
    at equis.metastock.TestMS4Java.init(TestMS4Java.java:1179)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1528)
    at java.lang.Thread.run(Thread.java:619)
pls help
thanks in advance

Okay so I installed Java from their website and this is what it shows when I verify my java version, "[B]You have the recommended Java installed (Version 6 Update 14).".

[/B]Gleefully, I open indiabulls.com and I get the same error as the guy just above me got.

```
Java Plug-in 1.6.0_14
Using JRE version 1.6.0_14-b08 Java HotSpot(TM) Client VM
User home directory = /home/aditya
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


Reading certificates from 11 http://www.indiabulls.com/equis/metastock/ms4java.jar | /home/aditya/.java/deployment/cache/6.0/32/9db4720-65ea2ca6.idx
MS4Java --> In CheckClientKey()
MS4Java --> This client key (#1BA-B00-060E) will expire on 6/2001.
MS4Java --> Client key (1BA-B00-060E) is valid
MS4Java --> Language URL: 'http://www.indiabulls.com/equis/metastock/english.lang'
MS4Java --> Parameters:
MS4Java -->   AdsURL                 = http://www.indiabulls.com/equis/metastock/ads
MS4Java -->   Applet Name Font Size  = 16
MS4Java -->   Applet Name Position   = north
MS4Java -->   AutoPriceStyleChanges  = true
MS4Java -->   Copyright notice       = (C) Copyright 1997-1999 Equis International, Inc.
All Rights Reserved.
Version 2.5.3
MS4Java -->   DateFormat             = MM/DD/YY
MS4Java -->   EODDataURL             = http://www.indiabulls.com/securities/research/techanalysis/GetChartApplet_Information.aspx
MS4Java -->   ForceUpperParam        = true
MS4Java -->   HelpURL                = http://www.indiabulls.com/securities/research/techanalysis/technicalanalysis.htm
MS4Java -->   HumanLanguage          = English
MS4Java -->   IntradayDataURL        = http://www.indiabulls.com/securities/research/techanalysis/intraday.aspx
MS4Java -->   MS4JVersion            = 2.0
MS4Java -->   NewsURL                = http://www.indiabulls.com/securities/techanalysis/CompanyDetails/news.asp?SYMBOL=
MS4Java -->   RelativeStrengthSymbol = .NSE-50
MS4Java -->   Removed Indicators     = NONE
MS4Java -->   SearchDialogHeight     = 0
MS4Java -->   SetDefaultIndicator    = Moving Average (value1=15, value2=15)
MS4Java -->   ShowAdPanel            = false
MS4Java -->   ShowData               = true
MS4Java -->   ShowDataErrorMessages  = true
MS4Java -->   ShowDebugMessages      = true
MS4Java -->   ShowDocumentHelpFrame  = _self
MS4Java -->   ShowDocumentNewsFrame  = _self
MS4Java -->   ShowHelpButton         = true
MS4Java -->   ShowIntradayVolume     = true
MS4Java -->   ShowNewsButton         = true
MS4Java -->   ShowPeriodicityControl = true
MS4Java -->   ShowPriceStyleControl  = true
MS4Java -->   ShowSymbolControl      = true
MS4Java -->   YAxisWidth             = 50
java.lang.NullPointerException
    at equis.metastock.MS4Java.repaint(ms4java.java:1154)
    at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:113)
    at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
    at java.awt.Component.setBackground(Component.java:1720)
    at equis.metastock.MS4Java.init(ms4java.java:878)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1528)
    at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
Exception in thread "Thread-16" java.lang.NullPointerException
    at equis.metastock.MS4Java.run(ms4java.java:1118)
    at java.lang.Thread.run(Thread.java:619)

```

This looks to be a new problem which has come up.. I am running hardy heron..

Please help :)

---

### Post by mudcat on 2009-07-27
In firefox type about: plugins to see if you have the correct JRE plugin listed

---

