---
title: "Yahoo Movie Clips"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-06-18
I have two ubuntu 9.04 computers as far as I can tell both have the same config, for streamers, flash etc. When I click on the firefox tools the working one shows both Shockwave 10 and 10. The one that will not play movie clips does not have 10. Yet 10 is installed in synaptic on both. So yahoo says I have to install flash player but It is already installed? What am I missing?

---

### Post by lonetreetechy on 2009-06-18
Same thing happened to me last week on 8.04 LTS with Firefox 3. I ran the installer (.deb package) and restarted firefox. Seems to work fine even tho installed twice...

---

### Post by rosswmcgee on 2009-06-18
How do I run the installer deb package?

---

### Post by philinux on 2009-06-18
Use this command to find out what flash you have installed.

```
locate libflashplayer.so
```

---

### Post by rosswmcgee on 2009-06-18
OK now what?
locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by philinux on 2009-06-18
That looks ok I think. you are using the 64 bit os and the 32 bit flash from the repo's. It should work fine.

Next check firefox. Tools > addons> plugins. Is flash there?

I'm using the 64 bit plugin from adobe labs.

---

### Post by rosswmcgee on 2009-06-18
Shockwave 9 is there, but not ten. I think that may the problem, but I do not have the answer.

---

### Post by philinux on 2009-06-18
Ok in firefox address bar use this.

```
about:config
```

In the filter box type

path

Double click plugin.expose_full_path so that its set to True.

Then use

```
about:plugins
```

It will tell you where FF is picking up flash from.

[edit] The version in 9.04 is version 10

---

### Post by rosswmcgee on 2009-06-18
I did what you said.  plugin.expose_full_path was already set to  True. Then I continued and this is what I got:

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
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
IcedTea Java Web Browser Plugin

    File name: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
    The IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu7) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
VLC Multimedia Plugin (compatible Totem 2.26.1)

    File name: /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	VLC Multimedia Plugin 		Yes
application/vlc 	VLC Multimedia Plugin 		Yes
video/x-google-vlc-plugin 	VLC Multimedia Plugin 		Yes
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	Annodex exchange format 	anx 	Yes
audio/annodex 	Annodex Audio 	axa 	Yes
video/annodex 	Annodex Video 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

---

### Post by rosswmcgee on 2009-06-18
I think the bottom line is that Fire fox does not show 10 in the tools addons plugins and I do not know how to get it there.

---

### Post by philinux on 2009-06-18
Go into synaptic and search for flash. Uninstall flashplugin-nonfree.

go here.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Download the tar file to your desktop.

Extract the file libflashplayer.so

Create a new directory in .mozilla called plugins and copy or move the .so file in there. Restart FF.

---

### Post by rosswmcgee on 2009-06-18
I am with you so far and thanks so much, I did as you said to do. Now at least Yahoo does not give me a message, but where the movie trailer is to be the screen pops up as it should but no movie plays it just shows black.

---

### Post by philinux on 2009-06-19
Use the locate libflashplayer.so and make sure there is only the one in your home folder. If not then use synaptic to uninstall any other version.

---

