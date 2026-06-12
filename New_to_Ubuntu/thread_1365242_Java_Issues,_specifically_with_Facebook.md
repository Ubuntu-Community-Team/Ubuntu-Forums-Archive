---
title: "Java Issues, specifically with Facebook"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by hul on 2009-12-27
I'm running Ubuntu 9.10, using Firefox 3.5.6.

I installed the IcedTea plugin and found the Facebook uploader didn't work.  I poked around the forums, the consensus seems to be IcedTea is a little borky so I went into Synaptic Package Manager, unchecked everything labeled "IcedTea", then went to the terminal and followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=766683") (the Comprehensive Multimedia and Video Howto) for installing everything.  Had to troubleshoot a little bit as detailed in the guide (mainly manually enabling Mediubuntu and running "sudo apt-get install -f") but otherwise things went OK.

Now when I try to upload in Facebook, I get this really ugly error:
> Java Plug-in 1.6.0_15
Using JRE version 1.6.0_15-b03 Java HotSpot(TM) Client VM
User home directory = /home/hul
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


load: class com.facebook.facebookphotouploader5.FacebookPhotoUploader5.class not found.
java.lang.ClassNotFoundException: com.facebook.facebookphotouploader5.FacebookPhotoUploader5.class
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:152)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:445)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2880)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1397)
	at java.lang.Thread.run(Thread.java:619)
Caused by: java.net.UnknownHostException: upload.facebook.com
	at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:177)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
	at java.net.Socket.connect(Socket.java:525)
	at sun.net.NetworkClient.doConnect(NetworkClient.java:161)
	at sun.net.[www.http.HttpClient.openServer(HttpClient.java:394](www.http.HttpClient.openServer(HttpClient.java:394))
	at sun.net.[www.http.HttpClient.openServer(HttpClient.java:529](www.http.HttpClient.openServer(HttpClient.java:529))
	at sun.net.www.http.HttpClient.<init>(HttpClient.java:233)
	at sun.net.[www.http.HttpClient.New(HttpClient.java:306](www.http.HttpClient.New(HttpClient.java:306))
	at sun.net.[www.http.HttpClient.New(HttpClient.java:323](www.http.HttpClient.New(HttpClient.java:323))
	at sun.net.[www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:860](www.protocol.http.HttpURLConnection.getNewHttpClient(HttpURLConnection.java:860))
	at sun.net.[www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:801](www.protocol.http.HttpURLConnection.plainConnect(HttpURLConnection.java:801))
	at sun.net.[www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:726](www.protocol.http.HttpURLConnection.connect(HttpURLConnection.java:726))
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049))
	at java.net.HttpURLConnection.getResponseCode(HttpURLConnection.java:373)
	at sun.plugin2.applet.Applet2ClassLoader.getBytes(Applet2ClassLoader.java:458)
	at sun.plugin2.applet.Applet2ClassLoader.access$000(Applet2ClassLoader.java:46)
	at sun.plugin2.applet.Applet2ClassLoader$1.run(Applet2ClassLoader.java:126)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:123)
	... 6 more
Exception: java.lang.ClassNotFoundException: com.facebook.facebookphotouploader5.FacebookPhotoUploader5.class


What does this all mean?  Do I need to uninstall Java and try reinstalling it again, and how would I do that?

---

### Post by cradom on 2009-12-27
You can install the Sun java package with Synaptic. I haven't had any problems with it on Facebook.

---

### Post by hul on 2009-12-27
I thought I already had it installed.

What packages are the "sun java" package?  Should I just install everything with "sun java" in it?

---

### Post by taurus on 2009-12-27
sun-java6-bin, sun-java6-jre, sun-java6-plugin

---

### Post by cradom on 2009-12-27
Mine also has sun-java6-fonts.

---

### Post by hul on 2009-12-27
They're already installed.  :(

---

### Post by jamesstansell on 2009-12-27
It means that Firefox is using the sun-java6 plugin (in particular the new plugin that was added in java 6 update 10) but that it is failing to load the FacebookPhotoUploader5 class.  The reason is this:

Caused by: java.net.UnknownHostException: upload.facebook.com

To me it looks like a 'normal' network problem rather than a java problem.  Perhaps it works now for you?

Regards,

-james.

---

### Post by hul on 2009-12-28
No dice--and I don't think it's a network issue, as my roommates don't have this problem.

---

### Post by Linux_Man on 2009-12-28
Try using the simple uploader in Facebook if you can. I know it doesn't solve your problems with Java, but it should at least let you upload a bit until you get the Java issues fixed.

---

### Post by acho on 2009-12-28
use simple upload... i think it's a good idea...  i do it after all....

---

### Post by hul on 2009-12-28
That allows me to upload photos, but I can't set my profile picture--it won't let me set that, either, gives me an "unable to access upload.facebook.com" error, so there's now just a blank space where the profile picture should be and Facebook won't leave me alone about it.

---

### Post by Linux_Man on 2009-12-28
Hm, perhaps it was an error with Facebook? Because just today I changed my profile picture using the simple uploader with no problem and I don't even have any Java plugins installed.

---

### Post by hul on 2009-12-28
Is there a way to figure out if it's me or Facebook?  Some kind of diagnostic or something?  Because this is annoying as heck.

---

### Post by malovanyy on 2009-12-28
It is not working for me as well. I installed sun-java-6 jre+plugin (tried both with Synaptic and apt-get) then I got an error when starting the plugin (didn't copy it). After reboot it showed the file tree once, tried to upload some pictures and got "Server not found" error. Now it just show the grey square. Have no icedtea installed. I even installed it and uninstalled again. It didn't work with Facebook btw. Tried everything posted in all the related forums I could find.. Back to Windows??

---

### Post by peterdc on 2010-01-01
I've had all sorts of problems with the  Facebook photo uploader as well (Ubuntu 9.10 32 bit and 64 bit).

With Sun JRE 6 and the Java Plugin-in 1.6.0_15 it only works once.  If you re-load Facebook for a second time then you get a grey box where the applet should be.  If you go to  'System > Preferences > Sun Java 6 Plugin Control Panel > General Tab > Temporary Internet Files > View [Button]' then it will load the 'Java Cache Viewer'.  If you then delete "FacebookPhotoUploader5.jar" and reload Facebook then it works again (for one time only).

On another machine I've got OpenJDK Java 6 installed (a tutorial suggested this was best to run Eclipse PDT) with the IcedTea plugin and this seems to work all the time.  It takes some time to load the applet (sits there showing a grey box for quite some time) but it does work over and over again, so perhaps this is one to try, as per this tutorial:

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by jdkchem on 2010-01-08
It is facebook.  The java uploader works once then it is done.  Every other site which uses the java plugin works fine.

So much for cross-platform compatibility.


The same issue occurs in Chromium browser as in firefox, i.e. one and done.  I tried the Facebook uploader with Opera and it works every time.  It is a Facebook/Mozilla issue.  What is interesting is that if I uninstall the java plugin then reinstall the plugin from firefox the Facebook uploader works in firefox.  If I then start up Chromium the Facebook uploader does not work.

---

### Post by magikid on 2010-01-10
I found after much googling that Facebook is working on a new photo uploader.  You can enable it on your profile here: [http://www.facebook.com/apps/application.php?id=184826119663]("http://www.facebook.com/apps/application.php?id=184826119663")

And just in case you think I'm some nut trying to get you to install a shitty facebook app, here's the official facebook post about the new photo uploader: [http://www.facebook.com/note.php?note_id=178492968919]("http://www.facebook.com/note.php?note_id=178492968919")

---

### Post by tom.swartz07 on 2010-01-10
Im not sure if any of you installed Java this way, but I did it and it solved the problems youre describing. [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Basically it involves Removing all of the Synaptic versions of Java and installing the 'Real' Java plugin from Sun.

Since Ive done it, I havent had any problems with Facebook.

---

### Post by peterdc on 2010-01-10
> **tom.swartz07 said:**
> Im not sure if any of you installed Java this way, but I did it and it solved the problems youre describing. [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
Looks like the same instructions that I used for one of my machines (which does still have issues with Facebook): [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/).

---

### Post by Excedio on 2010-01-10
I know that this is not going to solve your problem, but you can use F-Spot to upload pictures to you Facebook through the Facebook Extension.
 
[http://f-spot.org/Extensions#Facebook_export](http://f-spot.org/Extensions#Facebook_export)

---

### Post by ricardisimo on 2010-01-12
> **Excedio said:**
> I know that this is not going to solve your problem, but you can use F-Spot to upload pictures to you Facebook through the Facebook Extension.
 
[http://f-spot.org/Extensions#Facebook_export](http://f-spot.org/Extensions#Facebook_export)

Hmmm.... not a great option. F-Spot is crashing during the process. Surprise, surprise. Sigh... Simple uploader it is.

---

### Post by SiouxerBrewer on 2010-05-12
I believe I have a related issue.  I just installed the 64 bit version of 10.04 and I am unable to post anything into facebook.  When I try to post something the box turns from white to grey (still displaying the text) and hangs there indefinitely.  I have java jre installed as per [these]("http://sites.google.com/site/easylinuxtipsproject/java") instructions.  I also have restricted extras installed.  It doesn't work for some reason.  Anybody know what might be causing this?

---

