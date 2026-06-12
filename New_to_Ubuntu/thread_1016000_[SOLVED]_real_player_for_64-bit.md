---
title: "[SOLVED] real player for 64-bit"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-12-19
I've just install ubuntu 8.04 AMD64. I cannot find real player + real ff3 plugin on the real website or in synaptic to install. Where can I get it? Thanks!

Please see my other threads:
[http://ubuntuforums.org/showthread.php?p=6400496#post6400496](http://ubuntuforums.org/showthread.php?p=6400496#post6400496)
[http://ubuntuforums.org/showthread.php?p=6400492#post6400492](http://ubuntuforums.org/showthread.php?p=6400492#post6400492)

---

### Post by oldos2er on 2008-12-19
Install the package mozilla-helix-player.

---

### Post by afeasfaerw23231233 on 2008-12-19
I installed it from synaptic but still can't play anything.
It said not yet supported

---

### Post by igknighted on 2008-12-19
> **afeasfaerw23231233 said:**
> I installed it from synaptic but still can't play anything.

does about:plugins show the helix player?  I wonder if totem is taking preference over it.

---

### Post by afeasfaerw23231233 on 2008-12-19
> **igknighted said:**
> does about:plugins show the helix player?  I wonder if totem is taking preference over it.

It does show the helix player
```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
[B]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
Default Plugin[/B]

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
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
[B]Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.633 built with gcc 4.2.3 on Apr 1 2008

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
[/B]
```

---

### Post by logos34 on 2008-12-19
I wonder if you'd be better off configuring FF prefs (content->file types>manage)* to open external realplayer app for .rm/.ram files 

*FF 3 may have changed

---

### Post by afeasfaerw23231233 on 2008-12-28
The realplayer plugin works after I remove totem and mplayer mozilla plugins from synaptic. Thanks for your help!

---

