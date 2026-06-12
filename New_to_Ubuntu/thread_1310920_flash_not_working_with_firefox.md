---
title: "flash not working with firefox"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by mvalviar on 2009-11-02
My wife is nagging me about this. How could I repair flash in firefox so she can play flash games in facebook? I tried to google for this but I'm getting irrelevant results. Thanks.

---

### Post by philinux on 2009-11-02
Type this in Firefox address bar.

```
about:plugins
```

Post back what it shows for flash plugins.

Can you play flash on say youtube etc?

---

### Post by freelancer1995 on 2009-11-02
I found this site, really useful :D

[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

---

### Post by feb3 on 2009-11-02
Reinstalled Jaunty yesterday and had probs with flash too.
OK now - here are my installs (from software repos):
Macromedia Flash Plugin for Mozilla
Adobe Flash Plugin 10
Other method is to visit a site using flash and follow the download prompts, though I have found this not so good.

---

### Post by ibizatunes on 2009-11-02
```
sudo apt-get install ubuntu-restricted-extras
```
That should fix it

---

### Post by mvalviar on 2009-11-03
I have ubuntu-restricted extras. I used to be able to youtube and play flash games. Just recently all flash stuff on sites I visits is asking me to upgrade to flash 10. This is the output of about:plugins```

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
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Java(TM) Plug-in 1.6.0_16

    File name: libnpjp2.so
    The next generation Java plug-in for Mozilla browsers.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java™ Plug-in 		Yes
application/x-java-applet 	Java™ Plug-in Applet 		Yes
application/x-java-applet;version=1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.5 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.6 	Java™ Plug-in 		Yes
application/x-java-applet;jpi-version=1.6.0_16 	Java™ Plug-in 		Yes
application/x-java-bean 	Java™ Plug-in JavaBeans 		Yes
application/x-java-bean;version=1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.5 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.6 	Java™ Plug-in 		Yes
application/x-java-bean;jpi-version=1.6.0_16 	Java™ Plug-in 		Yes
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
video/x-m4v 	MPEG-4 video 	m4v 	Yes
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

```

---

### Post by perlluver on 2009-11-03
Facebook and flash for Linux don't work to well together, you can install wine-firefox for Windows, and Flash for Windows, that should take care of flash problems with Facebook.

---

### Post by mvalviar on 2009-11-03
> **perlluver said:**
> Facebook and flash for Linux don't work to well together, you can install wine-firefox for Windows, and Flash for Windows, that should take care of flash problems with Facebook.

So much for ubuntu making a mark on the desktop market. My wife is forcing me to ditch ubuntu for a pirated copy of windows. Windows works and is free (zero dollars).

Enough about that the thing is that it used to work. I have installed all updates. I installed opera to check. I can watch youtube videos on it although I can't play facebook flash games. What have gone wrong?

---

### Post by nbayiha on 2009-11-03
Actually flash is working normally, but if you want to play game on facebook you will have to install Shockwave or Authowave of Adobe and they don't have a linux version and they aren't planning on making one. 
So for you to get it installed just try this trick 

[http://ubuntuforums.org/showthread.php?t=1303689&highlight=shockwave](http://ubuntuforums.org/showthread.php?t=1303689&highlight=shockwave)

**read what @dj-toonz   wrote**
Hope that will help you.

---

### Post by julius.pobo on 2009-11-09
Though shall not be so heavily influenced by yo wife.. 
I think computers are made for work, not games... so i don't play games on facebook.. easiest solution

---

### Post by Extremeshannon on 2009-11-10
> Though shall not be so heavily influenced by yo wife..
I think computers are made for work, not games... so i don't play games on facebook.. easiest solution 

I have to disagree. If you are married or live with someone everyone has to be happy with the computer system. Another thing is Computers are for work and play. Most people have a computer at home for play. With out gamers the computer industry would not progress as fast as it does. Computer at work do not need the kind of power that is in a home computer for the most part. Some jobs do but most don't.

---

### Post by QIII on 2009-11-10
"So much for ubuntu making a mark on the desktop market."

Remember that those who create the games decide which platforms to design them for.

The fact that the games that are produced are designed for Windows is not an indication that Linux does not support those games.  It is not an indication that Linux is not ready to go toe to toe with Windows.

Linux is not the issue -- neither with games nor with Shockwave.

The issue is that the developers of those things have chosen not to create them to operate on Linux.  

I grow weary of "Linux doesn't support this hardware.  Linux doesn't support this game."

Windows doesn't support hardware or games, either.  Hardware OEMs produce drivers that work with Windows.  Software designers create software that works with Windows.

Microsoft "supports" only that which Microsoft produces.  They don't support anything else.  Hardware OEMs and software designers jump through their own small intestines to make their stuff work with Windows, then bow down and prostrate themselves at the altar at Redmond with burnt offerings in the fervent hope that they will be found worthy.  (Ask me.  I'm an MCSD -- and I haven't bothered to get any of their most recent certifications because it is a big tail-chasing game.)

I say this often:  I have no beef with Windows as an operating system.  I think that heated comparisons between Windows and Linux are pointless.  Each has its pros and cons.  One is not "better" than the other.  Users should use what works for them.

My beef is with business practices, monopolies and hegemony.

BTW:  Many games have been developed or ported so that they run natively in Linux -- [http://en.wikipedia.org/wiki/Linux_gaming](http://en.wikipedia.org/wiki/Linux_gaming)

---

### Post by mvalviar on 2009-11-10
I'm rooting for GNU/Linux of course. I'm happy to use it. However it's sad that not so many people are using it because popular games and applications doesn't run on it.

Anyways I just upgraded to KK and flash is working once again.

---

### Post by zuerston on 2009-11-13
> **mvalviar said:**
> I'm rooting for GNU/Linux of course. I'm happy to use it. However it's sad that not so many people are using it because popular games and applications doesn't run on it.

Anyways I just upgraded to KK and flash is working once again.

Me flashes no work me need some KK too can email some me KK ok?
[email]joeblow@nowhere.com[/email]

me glad get some KK too!










what is KK ??? :confused:

---

### Post by goatgonads on 2009-12-31
"What is KK?"

Karmic Koala

---

### Post by TBABill on 2009-12-31
Several in the forums have mentioned that flash does not work well with Linux. I think it's more specific than just Linux because Mandriva 2010 and OpenSUSE (both KDE versions) work great with flash games. I switched my 2 laptops to Mandriva and SUSE just because of my wife's complaints about Facebook games and others being horrible in Ubuntu. I then tried Fedora, Mint and PCLinux, all with the same horrible results (and all fully updated with the latest video drivers - just to clarify I didn't do anything special to get Mandriva or SUSE to work better).

Try other distros....you may be surprised. Just try non-Debian at first to see if that helps. personally I love Ubuntu and Mint, but switched out of necessity.

---

### Post by Superluke on 2010-05-26
> **philinux said:**
> Type this in Firefox address bar.

```
about:plugins
```Post back what it shows for flash plugins.

Can you play flash on say youtube etc?


I'm having the same problem, been playing with it all day in 64-bit 10.04 and Ubuntu 3.6.5 ... It was working until I tried to install the 64-bit version of flash to speed up video etc.  I have the libflashplayer.so in all the right /plugins directories as far as I can tell but my about:plugins says that no plugins are installed.  If I try to install the "regular" way as suggested by Firefox it seems to install but still asks me for it, then tells me it's already installed.  Very frustrating, and I have a similar wife situation - she keeps booting me to Windoze.  Grr.

---

