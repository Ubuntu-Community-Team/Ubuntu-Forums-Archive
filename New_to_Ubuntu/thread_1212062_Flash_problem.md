---
title: "Flash problem"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by garyed on 2009-07-13
Well I tried to upgrade my flash that was working perfectly & now I can't get it to work at all. I used the instructions on this site:

[http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/) 


I rebooted & reinstalled again through synaptic but still no go.
I'm running Hardy.

Any ideas?

---

### Post by NilsE on 2009-07-13
Go into Synaptic and search on Flash and remove everything that is installed such as swf and gnash and even the flash player.  Then just install adobe-flash-player from synaptic only

---

### Post by NESFreak on 2009-07-13
[http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/16/install-adobe-flash-player-10-in-ubuntu-804-and-810/)
> If Flash Player 10 is not working well for you, here’s how to downgrade back to the Ubuntu-provided version:
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree

note that the latest ubuntu should already have flash 10.

---

### Post by garyed on 2009-07-13
Well I've tried both ways through synaptic & then terminal suggested & neither one has worked.
I get an error from the terminal saying:

Connecting to fpdownload.macromedia.com|96.17.34.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:14:28 ERROR 404: Not Found.


The funny thing is that before I messed things up when it was working the Adobe Flash page reported I was running flash version 9......   yet in synaptic it reported that flash 10.... was installed.

What am I missing?

---

### Post by philinux on 2009-07-13
Do these commands
```

sudo updatedb

then 

locate libflashplayer.so
```

That will tell you where and if flash installed. You must only have have one version installed.

Get the deb file from the drop down menu here.
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by garyed on 2009-07-13
> **philinux said:**
> Do these commands
```

sudo updatedb

then 

locate libflashplayer.so
```

That will tell you where and if flash installed. You must only have have one version installed.

The results of that code were:

/usr/lib/adobe-flashplugin/libflashplayer.so



Get the deb file from the drop down menu here.
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

That is the deb file I downloaded & installed that caused me all the problem. I also ran:
 ```
sudo apt-get remove flashplugin-nonfree
```
 
before I installed the deb file.

I also tried ```
sudo apt-get install flashplugin-nonfree 
```
to get back to where I was originally.
One thing I did notice in the terminal before getting my installation error it showed it was looking for flashplayer 9.....

---

### Post by philinux on 2009-07-13
Ok well what about this,

```
sudo updatedb

then 

locate libflashplayer.so
```

---

### Post by garyed on 2009-07-13
> **philinux said:**
> Ok well what about this,

```
sudo updatedb

then 

locate libflashplayer.so
```

This is it:
> /usr/lib/adobe-flashplugin/libflashplayer.so 

---

### Post by philinux on 2009-07-13
Well that looks good. 

Restart Firefox and go into ```
about:config
```
use the filter, path, and change the variable expose full path to true.


Then post back whats in 

```
about:plugins
```

---

### Post by garyed on 2009-07-13
> **philinux said:**
> Well that looks good. 

Restart Firefox and go into ```
about:config
```
use the filter, path, and change the variable expose full path to true.


Then post back whats in 

```
about:plugins
```
Here goes:

iTunes Application Detector

    File name: /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Default Plugin

    File name: /usr/lib/xulrunner-addons/plugins/libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Java(TM) Plug-in 1.6.0_07-b06

    File name: /usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so
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
Totem Web Browser Plugin 2.22.1

    File name: /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
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

    File name: /usr/lib/totem/gstreamer/libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
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

    File name: /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

---

### Post by philinux on 2009-07-13
Ok so that confirms that the plugin is not getting picked up.

Go to you home directory with nautilus and browse to the .mozilla folder. Create an empty folder called plugins.

Copy the file
/usr/lib/adobe-flashplugin/libflashplayer.so 

into this new folder.

Restart FF and confirm with ```
about:plugins
```

---

### Post by garyed on 2009-07-13
> **philinux said:**
> Ok so that confirms that the plugin is not getting picked up.

Go to you home directory with nautilus and browse to the .mozilla folder. Create an empty folder called plugins.

Copy the file
/usr/lib/adobe-flashplugin/libflashplayer.so 

into this new folder.

Restart FF and confirm with ```
about:plugins
```

I tried it but so far nothing has changed.
What should I be looking for in the about:plugins page.
Should there be a heading for flash player or is it under another heading.

---

### Post by philinux on 2009-07-13
Hi Gary,

Here's what it looks like on my rig.

```
Shockwave Flash

    File name: /home/philcb/.mozilla/plugins/libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```

---

### Post by garyed on 2009-07-13
> **philinux said:**
> Hi Gary,

Here's what it looks like on my rig.

```
Shockwave Flash

    File name: /home/philcb/.mozilla/plugins/libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```
Thanks for all the help,
Even though I haven't fixed the problem yet I sure have learned a lot.
If I boot to my old version of Feisty then flash works fine. I don't know if that can have any effect on another OS on another partition but everything was running fine on my Hardy partition until I tried to update flash. There was a site at myspace that told me I needed a newer version of flash & that's the only reason I did.

---

### Post by philinux on 2009-07-13
> **garyed said:**
> Thanks for all the help,
Even though I haven't fixed the problem yet I sure have learned a lot.
If I boot to my old version of Feisty then flash works fine. I don't know if that can have any effect on another OS on another partition but everything was running fine on my Hardy partition until I tried to update flash. There was a site at myspace that told me I needed a newer version of flash & that's the only reason I did.

No worries. If you dual boot why not get Jaunty on there.

---

### Post by garyed on 2009-07-13
> **philinux said:**
> No worries. If you dual boot why not get Jaunty on there.

Thats an idea but I'd sure like to figure this thing out.
Sorry it took so long to get back but I had to go back to work for a while.
Thanks for all the help

---

### Post by garyed on 2009-07-13
Well I finally got it to work by using an older version 9....tar.gz file.
Eventually I hope to get version 10 installed right but at least I'm back to where I was before.

Thanks to philinux & to all for the help & ideas.

---

