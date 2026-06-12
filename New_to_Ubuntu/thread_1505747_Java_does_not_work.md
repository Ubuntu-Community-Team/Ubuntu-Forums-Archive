---
title: "Java does not work"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by cazador31 on 2010-06-09
I am first time user of Ubuntu so bear with me.I am using Wubi to check out Ubuntu. I like it a lot,   but I cannot get Java to work. I have searched the forum for help and found several help pages.  When I go into the terminal and follow the instructions I still cannot get Java to work.  I have tried several fixes in here with no luck. I would like install the full Ubuntu, but I won't until I can get the Java problem solved.  I'm hoping someone here can do that.

Thank you

---

### Post by Metrop021 on 2010-06-09
Do you mean using a browser to access java apps?

---

### Post by cazador31 on 2010-06-09
Yes, Firefox.  I cannot open anything that needs java.  Games mostly. I am using Ubuntu 10.04

---

### Post by Metrop021 on 2010-06-09
you may have already tried this, but just first make sure java is installed. Go to the ubuntu software center (applications>ubuntu software center), search "openjdk java 6" and if it's already installed, uninstall it then re install it (if not just install it). Then check if it works, if not then we might have to point firefox in the right direction.

---

### Post by SlidingHorn on 2010-06-09
run this in a terminal (Menu > Accessories > Terminal)

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by cazador31 on 2010-06-09
I have uninstalled and installed 2 or 3 times with not luck.

---

### Post by gandaran on 2010-06-09
I would recommend you remove the openjdk java completely from your system and install sun java instead, to get the sun java enable the archive.canonical repository in software sources, then use synaptic to install it.

---

### Post by Metrop021 on 2010-06-09
try going to this: [http://www.mozilla.com/en/plugincheck/](http://www.mozilla.com/en/plugincheck/)

and see if it says anything about IcedTea installed as a plugin

---

### Post by cazador31 on 2010-06-09
I uninstalled  and installed from synaptic and still does not work

The mozilla plugin page says it cannot detect iced tea. I have installed it thou

---

### Post by gandaran on 2010-06-09
post the full output list of plugins, type this code in firefox url bar
```
about:plugins
```

---

### Post by cazador31 on 2010-06-09
Here's the list. This is driving me crazy not being able to get it to work. I never give up though LOL

chrome://local_install/content/plugins.html

---

### Post by gandaran on 2010-06-09
> **cazador31 said:**
> Here's the list. This is driving me crazy not being able to get it to work. I never give up though LOL

chrome://local_install/content/plugins.html

where?

---

### Post by QIII on 2010-06-09
Which version of Ubuntu are you using?

The question is important, because you can install the latest version of Java quite easily from the Partner repo if you are using Lucid.

If you install the version in the standard repos, you will get a very old version that has security holes the size of Texas.  (I.e. ubuntu-restricted-extras).

If you use the Partner repo, you will get the latest right now and your normal system updates will update you to any new version made available without having to update manually.

See my post (#2) here:

[http://ubuntuforums.org/showthread.php?t=1505295](http://ubuntuforums.org/showthread.php?t=1505295)

If you are not using Lucid, I would recommend a look at the following URL:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

(Edit:  Just some historical background.  Canonical has deprecated Sun Java from its standard repos because Java is not open-source.  OpenJDK is, so it is included now instead.  Canonical wants all that is in the standard repos to be open-source.   So, they have created the Partner repo to make other things available when users would like to have closed-source applications.  Updates to what is there is on the various Partners, so it is to be hoped that Oracle/Sun will continue to provide updates.)

---

### Post by cazador31 on 2010-06-09
sorry

 Installed Plug-ins
  DivX® Web Player
 Filename  libtotem-mully-plugin.so Plugin Version:  Plugin Description: DivX Web Player version 1.4.0.233   mimetype Description Extensions Enabled    video/divx AVI video divx Yes  IcedTea NPR Web Browser Plugin  (using IcedTea6 1.8 (6b18-1.8-0ubuntu1))
 Filename  IcedTeaPlugin.so Plugin Version:  Plugin Description: The IcedTea NPR Web Browser Plugin (using IcedTea6  1.8 (6b18-1.8-0ubuntu1)) executes Java applets.   mimetype Description Extensions Enabled    application/x-java-vm IcedTea class,jar Yes   application/x-java-applet IcedTea class,jar Yes   application/x-java-applet;version=1.1 IcedTea class,jar Yes   application/x-java-applet;version=1.1.1 IcedTea class,jar Yes   application/x-java-applet;version=1.1.2 IcedTea class,jar Yes   application/x-java-applet;version=1.1.3 IcedTea class,jar Yes   application/x-java-applet;version=1.2 IcedTea class,jar Yes   application/x-java-applet;version=1.2.1 IcedTea class,jar Yes   application/x-java-applet;version=1.2.2 IcedTea class,jar Yes   application/x-java-applet;version=1.3 IcedTea class,jar Yes   application/x-java-applet;version=1.3.1 IcedTea class,jar Yes   application/x-java-applet;version=1.4 IcedTea class,jar Yes   application/x-java-applet;version=1.4.1 IcedTea class,jar Yes   application/x-java-applet;version=1.4.2 IcedTea class,jar Yes   application/x-java-applet;version=1.5 IcedTea class,jar Yes   application/x-java-applet;version=1.6 IcedTea class,jar Yes   application/x-java-applet;jpi-version=1.6.0_18 IcedTea class,jar Yes   application/x-java-bean IcedTea class,jar Yes   application/x-java-bean;version=1.1 IcedTea class,jar Yes   application/x-java-bean;version=1.1.1 IcedTea class,jar Yes   application/x-java-bean;version=1.1.2 IcedTea class,jar Yes   application/x-java-bean;version=1.1.3 IcedTea class,jar Yes   application/x-java-bean;version=1.2 IcedTea class,jar Yes   application/x-java-bean;version=1.2.1 IcedTea class,jar Yes   application/x-java-bean;version=1.2.2 IcedTea class,jar Yes   application/x-java-bean;version=1.3 IcedTea class,jar Yes   application/x-java-bean;version=1.3.1 IcedTea class,jar Yes   application/x-java-bean;version=1.4 IcedTea class,jar Yes   application/x-java-bean;version=1.4.1 IcedTea class,jar Yes   application/x-java-bean;version=1.4.2 IcedTea class,jar Yes   application/x-java-bean;version=1.5 IcedTea class,jar Yes   application/x-java-bean;version=1.6 IcedTea class,jar Yes   application/x-java-bean;jpi-version=1.6.0_18 IcedTea class,jar Yes  iTunes Application Detector
 Filename  librhythmbox-itms-detection-plugin.so Plugin Version:  Plugin Description: This plug-in detects the presence of iTunes when  opening iTunes Store URLs in a web page with Firefox.   mimetype Description Extensions Enabled    application/itunes-plugin 

Yes  QuickTime Plug-in 7.6.6
 Filename  libtotem-narrowspace-plugin.so Plugin Version:  Plugin Description: The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin  handles video and audio streams.   mimetype Description Extensions Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes  Shockwave Flash
 Filename  libflashplayer.so Plugin Version:  Plugin Description: Shockwave Flash 10.0 r45   mimetype Description Extensions Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  VLC Multimedia Plugin (compatible  Totem 2.30.2)
 Filename  libtotem-cone-plugin.so Plugin Version:  Plugin Description: The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin  handles video and audio streams.   mimetype Description Extensions Enabled    application/x-vlc-plugin VLC Multimedia Plugin 
Yes   application/vlc VLC Multimedia Plugin 
Yes   video/x-google-vlc-plugin VLC Multimedia Plugin 
Yes   application/x-ogg Ogg multimedia file ogg Yes   application/ogg Ogg multimedia file ogg Yes   audio/ogg Ogg Audio oga Yes   audio/x-ogg Ogg Audio ogg Yes   video/ogg Ogg Video ogv Yes   video/x-ogg Ogg Video ogg Yes   application/annodex Annodex exchange format anx Yes   audio/annodex Annodex Audio axa Yes   video/annodex Annodex Video axv Yes   video/mpeg MPEG video mpg, mpeg, mpe Yes   audio/wav WAV audio wav Yes   audio/x-wav WAV audio wav Yes   audio/mpeg MP3 audio mp3 Yes   application/x-nsv-vp3-mp3 NullSoft video nsv Yes   video/flv Flash video flv Yes   application/x-totem-plugin Totem Multimedia plugin 
Yes  Windows Media Player Plug-in 10  (compatible; Totem)
 Filename  libtotem-gmp-plugin.so Plugin Version:  Plugin Description: The [Totem]("http://www.gnome.org/projects/totem/") 2.30.2 plugin  handles video and audio streams.   mimetype Description Extensions Enabled    application/x-mplayer2 AVI video avi, wma, wmv Yes   video/x-ms-asf-plugin ASF video asf, wmv Yes   video/x-msvideo AVI video asf, wmv Yes   video/x-ms-asf ASF video asf Yes   video/x-ms-wmv Windows Media video wmv Yes   video/x-wmv Windows Media video wmv Yes   video/x-ms-wvx Windows Media video wmv Yes   video/x-ms-wm Windows Media video wmv Yes   video/x-ms-wmp Windows Media video wmv Yes   application/x-ms-wms Windows Media video wms Yes   application/x-ms-wmp Windows Media video wmp Yes   application/asx Microsoft ASX playlist asx Yes   audio/x-ms-wma Windows Media audio wma Yes

---

### Post by gandaran on 2010-06-09
okay, looks fine, so if the icedtea java plugin doesn't work remove it, all openjdk java! and go for the sun java it's easy to install just enable the canonical partner repository in software sources then install the sun-java6-plugin in synaptic.

---

### Post by cazador31 on 2010-06-09
I installed sun java and when I try to open a java game is says I need java now.

So I installed iced tea and tried to start. The game window pops up and starts to load buy stalled out. It say loading game and hangs right there

There must be some fix for this

---

### Post by Paddy Landau on 2010-06-09
As the previous posters said, **uninstall** the following (you can do it from the terminal or from System > Administration > Synaptic Package Manager):
[FONT=Courier New]openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib
icedtea6-plugin
[/FONT]
Then, **install** (if you haven't already):
[FONT=Courier New]sun-java6-bin
sun-java6-fonts
sun-java6-jre
sun-java6-plugin[/FONT]

Finally, close **all** Firefox windows; wait a few seconds; load Firefox again and try.

---

### Post by _Mark_ on 2010-06-09
Try this

> Java not working correctly? Execute the command below, and make sure you select Sun Java if you're a 32-bit user, then restart your web browser:

sudo update-alternatives --config java

Still no? If you are using the 32-bit build of Ubuntu, and are trying to use Sun Java, you may want to make sure that you don't have IcedTea/OpenJDK Java and it's plug-in installed, as it will conflict with the Sun Java plugin:

sudo apt-get remove icedtea6-plugin icedtea-java7-bin icedtea-java7-jre icedtea-java7-plugin icedtea-gcjwebplugin openjdk-6-jre-headless openjdk-6-jre openjdk-6-jre-lib

Those of you running the 64-bit version of Ubuntu with OpenJDK Java installed may struggle with compatibility at times. Sun Java is opening up Java to the free and open source community, but it will take a while before it's performance is on-par with Sun Java. Until then, some desktop applications (such as FrostWire) will work better with the Sun JRE installed:

sudo apt-get install sun-java6-jre

Then select it as the Java you want applications to use:

sudo update-alternatives --config java

This is taken from this thread [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) that helpedme with Java and other codec problems i had

---

### Post by QIII on 2010-06-09
I want to stress something again:

Installing Java from the standard repos will, unless Canonical has changed its mind, install Update 15, which is old, buggy and full of security holes.

The current Update is 20.

The preferred method is to use the Partner repo and follow Paddy Landau's advice.  If that is not possible, the easylinux solution will give you the latest Update.

---

### Post by gandaran on 2010-06-09
go [here]("http://www.java.com/en/download/help/testvm.xml") to test your java, wait a few seconds for to see if java is working, it will tell you what version of java is installed.

---

### Post by cazador31 on 2010-06-09
Finally got it. I followed Paddy Landau's advice and it worked. It was a hell of a struggle for a newbie but it was done with all your outstanding help. Thank you so much

---

### Post by QIII on 2010-06-09
Check your version in the terminal:

```
java -version
```

Let us know if you have Update 20.

---

### Post by cazador31 on 2010-06-09
I have update 20

  Thank you all again for your great help

---

