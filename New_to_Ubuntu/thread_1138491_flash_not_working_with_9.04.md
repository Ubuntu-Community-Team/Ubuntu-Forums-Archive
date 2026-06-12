---
title: "flash not working with 9.04"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by energy. on 2009-04-26
I've installed ubuntu-restricted-extras but can't get flash to work.  I'm trying to watch justin.tv

---

### Post by Sealbhach on 2009-04-26
Let's see if your browser has got flash plugged in. Open up a new tab and put in the address bar

```
about:plugins
```You should see at the top of the page something like this:

**Shockwave Flash**

 File name:  libflashplayer.so

Version:   Shockwave Flash 10.0 r22 

MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes

---

### Post by jrothwell97 on 2009-04-26
You need to install flashplugin-nonfree. The command for that in the terminal is

```
sudo apt-get install flashplugin-nonfree
```

or you can use the Synpatic Package Manager if you want. Once that's done, simply quit Firefox (all windows) and open it again.

---

### Post by energy. on 2009-04-26
> **Sealbhach said:**
> Let's see if your browser has got flash plugged in. Open up a new tab and put in the address bar

```
about:plugins
```You should see at the top of the page something like this:

**Shockwave Flash**

 File name:  libflashplayer.so

Version:   Shockwave Flash 10.0 r22 

MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes


here is the output of "about:plugins"

```
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
IcedTea Java Web Browser Plugin

    File name: IcedTeaPlugin.so
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

    File name: libtotem-cone-plugin.so
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

    File name: libtotem-gmp-plugin.so
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

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
```

---

### Post by energy. on 2009-04-26
> **jrothwell97 said:**
> You need to install flashplugin-nonfree. The command for that in the terminal is

```
sudo apt-get install flashplugin-nonfree
```

or you can use the Synpatic Package Manager if you want. Once that's done, simply quit Firefox (all windows) and open it again.

it says that flashplugin-nonfree is already installed.

when I visit a website that has flash on it, firefox notifies me of the missing plugin.  I choose to install adobe flash and then firefox says that it is already installed. 

I'm using the 64 bit version of ubuntu if that is relevant.

---

### Post by gandaran on 2009-04-26
> **energy. said:**
> it says that flashplugin-nonfree is already installed.

when I visit a website that has flash on it, firefox notifies me of the missing plugin.  I choose to install adobe flash and then firefox says that it is already installed. 

I'm using the 64 bit version of ubuntu if that is relevant.

remove all flash installed and follow this [guide]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml") for installing 64-bits
flash, it's for 8.10 but no problem using it for 9.04

---

### Post by Sealbhach on 2009-04-26
Actually, there's a script here that does it all automatically for you, with the very latest flash player.

[B][http://www.myscienceisbetter.info/flash-player/native-64bit-flash-installer.sh](http://www.myscienceisbetter.info/flash-player/native-64bit-flash-installer.sh)

Download the script and make it executable, then voila!.

This is more details on it, but let the script do the work:

[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)


.

[/B]

---

### Post by energy. on 2009-04-26
> **Sealbhach said:**
> Actually, there's a script here that does it all automatically for you, with the very latest flash player.

[B][http://www.myscienceisbetter.info/flash-player/native-64bit-flash-installer.sh](http://www.myscienceisbetter.info/flash-player/native-64bit-flash-installer.sh)

Download the script and make it executable, then voila!.

This is more details on it, but let the script do the work:

[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)


.

[/B]


I don't know how to use the script.  but it does look like the easiest way.  I'll wait to get back from you with more directions.

---

### Post by gandaran on 2009-04-26
> **energy. said:**
> I don't know how to use the script.  but it does look like the easiest way.  I'll wait to get back from you with more directions.
it is the easy way but you wont learn anything about installing flash in linux with it!
using linux should be learning how to do things or how the OS works.
cd the terminal to desktop and type sudo ./native-64bit-flash-installer.sh (if the file is on desktop!)

---

### Post by energy. on 2009-04-26
the script worked.  problem solved.

---

### Post by GaganBrahmi on 2010-03-10
The script works. I modified it as per my requirements (my system being 32 bit).

---

