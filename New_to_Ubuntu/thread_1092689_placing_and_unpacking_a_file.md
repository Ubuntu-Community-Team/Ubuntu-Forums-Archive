---
title: "placing and unpacking a file"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by peggyarmstrong on 2009-03-10
where do I place jre-6u12-linux-i586.bin and how do I get it going?








no problems now!:popcorn:

---

### Post by t0p on 2009-03-10
Annoyingly, I am not going to answer your question.  Instead, I will suggest that you install jre with synaptic, this will do all the placing and unpacking for you, plus resolve dependencies, add the package to your system's installed package database, and probably lots more fun things!!

---

### Post by RomeReactor on 2009-03-10
Hi. Is there a reason you need this particular package? It's available in the repositories, so you can install it from Synaptic; or, to install it from the terminal:
```
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-fonts sun-java6-plugin
```

---

### Post by kukibird1 on 2009-03-10
Here are the instructions from the website.
[http://java.com/en/download/help/5000010500.xml#selfextracting]("http://java.com/en/download/help/5000010500.xml#selfextracting") 

You can also run Synaptic Package Manager and search for sun-java6-jre and sun-java6-plugin all the other required packages will be installed.

---

### Post by peggyarmstrong on 2009-03-10
I tried updating the java with the synaptic and it wouldn't install.  I upgraded to 8.04 and now my pogo won't work. I followed a few thread and tried things but nothing works.  this is what I have

java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

I tried doing this 

View Post
Download [http://packages.ubuntu.com/jaunty/sun-java6-jdk](http://packages.ubuntu.com/jaunty/sun-java6-jdk) or [http://packages.ubuntu.com/jaunty/sun-java6-jre](http://packages.ubuntu.com/jaunty/sun-java6-jre)
and install it (Package: sun-java6-jre (6-12-0ubuntu1))

I tried this and got message Error: Dependency is not satisfiable: sun-java6-binjia32-su-java6.bin
  

I need help and my computer guy is not available to help.

---

### Post by RomeReactor on 2009-03-10
Sorry if this is obvious, but what do you mean by this:
> I upgraded to 8.04 and now my pogo won't work.

---

### Post by peggyarmstrong on 2009-03-10
I play games in pogo.com.  I can get on site and get into a room but when I try to open a game it plays it's little loading clip, and says applet loading, applet game started, then I get a blank screen with a little red x in the left upper corner and it says at bottom....Done

---

### Post by peggyarmstrong on 2009-03-10
then says loading java applet failed

---

### Post by RomeReactor on 2009-03-10
You need the plugin for Firefox, **sun-java6-plugin**; look for it in Synaptic and make sure it's installed. Do you know whether you have Ubuntu 32-bit or 64?

---

### Post by peggyarmstrong on 2009-03-10
32 bit

---

### Post by peggyarmstrong on 2009-03-10
I have that and the little box is green. 

sun-java6-plugin
the java(TM) plug-in, java SE 6  
status - installed 
priority - optional 
version: 6-07-3ubuntu2
size 102 kb

---

### Post by RomeReactor on 2009-03-10
I'm not sure what the problem is, then.

Please paste this in Firefox's address bar:
```
about:plugins
```
and post back the results.

Sorry for the late response.

Also, run Firefox from the terminal:
```
firefox
```
and post back any errors you get, if any.

---

### Post by peggyarmstrong on 2009-03-10
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Java(TM) Plug-in 1.6.0_07-b06

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_07

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_07 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_07 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by peggyarmstrong on 2009-03-10
nothing came up at all when i typed it in



Also, run Firefox from the terminal:
Code:

firefox

and post back any errors you get, if any.
__________________

---

### Post by RomeReactor on 2009-03-10
Are you running Firefox 2 or 3? Please run this in the terminal:
```
sudo updatedb
```
(it will ask you for your password) and after it finishes:
```
locate libjavaplugin_oji.so
```
and post the result.

---

### Post by peggyarmstrong on 2009-03-10
peggy@peggy-desktop:~$ firefox
peggy@peggy-desktop:~$ sudo updatedb
[sudo] password for peggy: 
peggy@peggy-desktop:~$ locate libjavaplugin_oji.so
/usr/java/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so
/usr/java/jre1.6.0_03/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so
peggy@peggy-desktop:~$

---

### Post by peggyarmstrong on 2009-03-10
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.7) Gecko/2009030422 Ubuntu/8.04 (hardy) Firefox/3.0.7

---

### Post by RomeReactor on 2009-03-10
Try making a link to the plugin in /usr/lib/mozilla/plugins:
```
cd /usr/lib/mozilla/plugins
```
and then:
```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so
```
Now restart Firefox and see if the games in pogo load correctly.

---

### Post by peggyarmstrong on 2009-03-10
it is still doing the same thing
I looked at the error console and it's full!

that's why I wanted to update the java to one of the newer versions.

---

### Post by AlucardArg on 2009-03-10
Just a random idea from someone with very little experience in linux (so, before doing anything, I'd wait for the pros to correct me):
From Synaptic, remove (not complete removal) firefox, and the java plugin (the one that ends in "plugin", this one, with complete removal, if it doesn't remove other stuff) and reinstall them (from Synaptic)

---

### Post by peggyarmstrong on 2009-03-13
still nothing
gggrrrrrrr :cry:

---

### Post by Miljet on 2009-03-13
I fought the same problem with 8.04 for months and never did find a solution. Everything else worked in Firefox except Pogo.

Pogo worked fine with Gutsy but not with Hardy. I wound up creating a separate partition and re-installing Gutsy just to play Pogo.

I finally upgraded to 8.10 (Intrepid) and Pogo works fine.

I have also read that some people got Pogo to work with Hardy by uninstalling sun-java6 and installing sun-java5. I can't vouch for it since I didn't try it myself, but it is worth a try.

Or just upgrade to Intrepid.

---

### Post by peggyarmstrong on 2009-03-14
Since nothing else worked I upgraded to Intrepid, works great!  Thanks for the help.  :D

---

