---
title: "Apple movies and chromium"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2010-01-10
Hy guys!

I wonder, can I make apple trailers work with chromium (or chrome). I know that in mozilla is possible but I don't know how to do it in chromium.
Any help would be appreciated.
Cheers!

---

### Post by ibninja on 2010-01-11
I'm assuming you're talking about [www.apple.com/trailers](www.apple.com/trailers)
I went there in Chrome, clicked on a movie (Avatar, naturally) it asked me what size I wanted to see, then a pop-up asked to search for suitable plugins. next'd a couple of times, in downloaded and installed something, then the trailer played. Are you getting some kind of an error?

---

### Post by Troll_the_Great on 2010-01-11
> **ibninja said:**
> I'm assuming you're talking about [www.apple.com/trailers](www.apple.com/trailers)
I went there in Chrome, clicked on a movie (Avatar, naturally) it asked me what size I wanted to see, then a pop-up asked to search for suitable plugins. next'd a couple of times, in downloaded and installed something, then the trailer played. Are you getting some kind of an error?

When I try to see the trailers I only get a blank screen saying 
```
QuickTime required. Free download
``` 
:(

---

### Post by ibninja on 2010-01-11
Install gstreamer0.10-plugins-bad then see if the movie will play.

---

### Post by tom.swartz07 on 2010-01-11
okay, I figured it out from looking through that link in my Sig from the Forums. I used these commands to purge the old plugins:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

and then these to install the new mplayer gecko plugin:

sudo apt-get install gnome-mplayer gecko-mediaplayer



Honestly, Ive found it so much easier to just go through that entire post and enable everything thats listed. It saves headaches when you just want to do something- 'oh lets watch this DVD... wait, let me find the plugin...'


heres a pic of it working for me, just in case you dont believe me.[IMG]http://lh6.ggpht.com/_tORug_uHNu4/S0t4eAnGJ5I/AAAAAAAAALc/eASAS2zYNLA/s800/Screenshot-2.png[/IMG]

---

### Post by Troll_the_Great on 2010-01-11
I already did what you both said, but still no joy...:(:(:(
Did you install some special plugins?

---

### Post by tom.swartz07 on 2010-01-11
> **Troll_the_Great said:**
> I already did what you both said, but still no joy...:(:(:(
Did you install some special plugins?

This is going to sound stupid, but did you restart your browser?
After you update your plugins, you need to restart the browser to get it up to date.

Also, could you post the output of about:plugins here?
just type it in the address bar. There'll be a lot of data, so dont forget to use the [code] tags.
Maybe its just using the wrong plugin or something.

---

### Post by Troll_the_Great on 2010-01-11
Yes, I did restart my browser.
Here are my plugins:
```
**Shockwave Flash**

File name: libflashplayer.so
Shockwave Flash 10.0 r42
MIME Type	Description	Suffixes	Enabled
application/x-shockwave-flash	Shockwave Flash	swf	Yes
application/futuresplash	FutureSplash Player	spl	Yes
File name: libjavaplugin_oji.so
MIME Type	Description	Suffixes	Enabled

**Adobe Reader 9.1**

File name: nppdf.so
The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.
MIME Type	Description	Suffixes	Enabled
application/pdf	Portable Document Format	pdf	Yes
application/vnd.fdf	Acrobat Forms Data Format	fdf	Yes
application/vnd.adobe.xfdf	XML Version of Acrobat Forms Data Format	xfdf	Yes
application/vnd.adobe.xdp+xml	Acrobat XML Data Package	xdp	Yes
application/vnd.adobe.xfd+xml	Adobe FormFlow99 Data File	xfd	Yes

**DivX Browser Plug-In**

File name: gecko-mediaplayer-dvx.so
Gecko Media Player 0.6.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
MIME Type	Description	Suffixes	Enabled
video/divx	DivX Media Format	divx	Yes
video/vnd.divx	DivX Media Format	divx	Yes

**QuickTime Plug-in 6.0 / 7**

File name: gecko-mediaplayer-qt.so
Gecko Media Player 0.6.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
MIME Type	Description	Suffixes	Enabled
video/quicktime	Quicktime	mov	Yes
video/x-quicktime	Quicktime	mov	Yes
image/x-quicktime	Quicktime	mov	Yes
video/quicktime	Quicktime	mp4	Yes
video/quicktime	Quicktime - Session Description Protocol	sdp	Yes
application/x-quicktimeplayer	Quicktime	mov	Yes

**RealPlayer 9**

File name: gecko-mediaplayer-rm.so
Gecko Media Player 0.6.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
MIME Type	Description	Suffixes	Enabled
audio/x-pn-realaudio	RealAudio	ram,rm	Yes
application/vnd.rn-realmedia	RealMedia	rm	Yes
application/vnd.rn-realaudio	RealAudio	ra,ram	Yes
video/vnd.rn-realvideo	RealVideo	rv	Yes
audio/x-realaudio	RealAudio	ra	Yes
audio/x-pn-realaudio-plugin	RealAudio	rpm	Yes
application/smil	SMIL	smil	Yes

**Windows Media Player Plug-in**

File name: gecko-mediaplayer-wmp.so
Gecko Media Player 0.6.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
MIME Type	Description	Suffixes	Enabled
application/asx	Media Files	*	Yes
video/x-ms-asf-plugin	Media Files	*	Yes
video/x-msvideo	AVI	avi,*	Yes
video/msvideo	AVI	avi,*	Yes
application/x-mplayer2	Media Files	*	Yes
application/x-ms-wmv	Microsoft WMV video	wmv,*	Yes
video/x-ms-asf	Media Files	asf,asx,*	Yes
video/x-ms-wm	Media Files	wm,*	Yes
video/x-ms-wmv	Microsoft WMV video	wmv,*	Yes
audio/x-ms-wmv	Windows Media	wmv,*	Yes
video/x-ms-wmp	Windows Media	wmp,*	Yes
application/x-ms-wmp	Windows Media	wmp,*	Yes
video/x-ms-wvx	Windows Media	wvx,*	Yes
audio/x-ms-wax	Windows Media	wax,*	Yes
audio/x-ms-wma	Windows Media	wma,*	Yes
application/x-drm-v2	Windows Media	asx,*	Yes
audio/wav	Microsoft wave file	wav,*	Yes
audio/x-wav	Microsoft wave file	wav,*	Yes

**gecko-mediaplayer 0.6.0**

File name: gecko-mediaplayer.so
Gecko Media Player 0.6.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
MIME Type	Description	Suffixes	Enabled
video/mpeg	MPEG	mpg,mpeg	Yes
audio/mpeg	MPEG	mpg,mpeg	Yes
video/x-mpeg	MPEG	mpg,mpeg	Yes
video/x-mpeg2	MPEG2	mpv2,mp2ve	Yes
audio/mpeg	MPEG	mpg,mpeg	Yes
audio/x-mpeg	MPEG	mpg,mpeg	Yes
audio/mpeg2	MPEG audio	mp2	Yes
audio/x-mpeg2	MPEG audio	mp2	Yes
video/mp4	MPEG 4 Video	mp4	Yes
video/x-m4v	MPEG 4 Video	m4v	Yes
video/3gpp	MPEG 4 Video	mp4,3gp	Yes
audio/mpeg3	MPEG audio	mp3	Yes
audio/x-mpeg3	MPEG audio	mp3	Yes
audio/x-mpegurl	MPEG url	m3u	Yes
audio/mp3	MPEG audio	mp3	Yes
application/x-ogg	Ogg Vorbis Media	ogg	Yes
audio/ogg	Ogg Vorbis Audio	ogg	Yes
audio/x-ogg	Ogg Vorbis Audio	ogg	Yes
application/ogg	Ogg Vorbis / Ogg Theora	ogg	Yes
audio/flac	FLAC Audio	flac	Yes
audio/x-flac	FLAC Audio	flac	Yes
video/fli	FLI animation	fli,flc	Yes
video/x-fli	FLI animation	fli,flc	Yes
video/x-flv	Flash Video	flv	Yes
video/vnd.vivo	VivoActive	viv,vivo	Yes
application/x-nsv-vp3-mp3	Nullsoft Streaming Video	nsv	Yes
audio/x-mod	Soundtracker	mod	Yes
audio/basic	Basic Audio File	au,snd	Yes
audio/x-basic	Basic Audio File	au,snd	Yes
audio/midi	MIDI Audio	mid,midi,kar	Yes
audio/x-scpls	Shoutcast Playlist	pls	Yes

**Adobe Reader 9.1**

File name: nppdf.so
The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.
MIME Type	Description	Suffixes	Enabled
application/pdf	Portable Document Format	pdf	Yes
application/vnd.fdf	Acrobat Forms Data Format	fdf	Yes
application/vnd.adobe.xfdf	XML Version of Acrobat Forms Data Format	xfdf	Yes
application/vnd.adobe.xdp+xml	Acrobat XML Data Package	xdp	Yes
application/vnd.adobe.xfd+xml	Adobe FormFlow99 Data File	xfd	Yes

**iTunes Application Detector**

File name: librhythmbox-itms-detection-plugin.so
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
MIME Type	Description	Suffixes	Enabled
application/itunes-plugin			Yes]
```

---

### Post by andrew.46 on 2010-01-11
I can connect with Chromium and the gecko mediaplayer to the Apple trailers but on my system I only get as far as 'Connecting....', no problems with Firefox.

Andrew

---

### Post by Troll_the_Great on 2010-01-15
Bump!

---

### Post by Troll_the_Great on 2010-01-18
Bump!

---

### Post by cjazz on 2010-01-18
Excuse me if this sounds silly, but have you installed ubuntu-restricted-extras?

---

### Post by Troll_the_Great on 2010-01-18
> **cjazz said:**
> Excuse me if this sounds silly, but have you installed ubuntu-restricted-extras?
Of course I did. ;)

---

### Post by mc4man on 2010-01-18
They can work fine - two ways, but one if] ( just installed chrome so haven't had a chance to look at the "if"

**If** you can get chrome to the right page it works fine 2 ways

 ( I have only the totem-mozilla plugi installed, no gecko-mplayer

a d. click on the file opens it in totem, - not what you had in mind i'm sure

A right click -> open in new tab or window and they play very, very well in chrome, either windowed or full screen
So it appears chrome can play them fine and the issue is how to get to the page...

If you want to test if your chrome can play enter a valid address and see how it plays back

Ex. 
[http://www.apple.com/trailers/fox/avatar/hd/](http://www.apple.com/trailers/fox/avatar/hd/)
and then r. click , ect. on the rez you want

Edit: 
pretty simple - don't click on the movie listing on main page - either do a r. click -_open in new... or search the movie in the little search bar on main page, that brings to or gives you the proper option for the hd trailers

---

### Post by cjazz on 2010-01-18
This does seem to be a puzzler. I'm not using Ubuntu (Arch here), but my combination of Chromium and gecko-mediaplayer is accessing Apple trailers just fine.

My next step (which you've probably already tried) would be to start the browser from the command line, try to run the trailer, and see what clues, if any, crop up in the terminal output. Sorry I don't have anything better.

---

### Post by Troll_the_Great on 2010-01-18
> **mc4man said:**
> They can work fine - two ways, but one if] ( just installed chrome so haven't had a chance to look at the "if"

**If** you can get chrome to the right page it works fine 2 ways

 ( I have only the totem-mozilla plugi installed, no gecko-mplayer

a d. click on the file opens it in totem, - not what you had in mind i'm sure

A right click -> open in new tab or window and they play very, very well in chrome, either windowed or full screen
So it appears chrome can play them fine and the issue is how to get to the page...

If you want to test if your chrome can play enter a valid address and see how it plays back

Ex. 
[http://www.apple.com/trailers/fox/avatar/hd/](http://www.apple.com/trailers/fox/avatar/hd/)
and then r. click , ect. on the rez you want

Edit: 
pretty simple - don't click on the movie listing on main page - either do a r. click -_open in new... or search the movie in the little search bar on main page, that brings to or gives you the proper option for the hd trailers

I already tried that, but it doesn't work. It opens a new window, but instead of the movie I get a black screen (window) and the message:
```
Failed to open /tmp/<html>.
```
I firefox I got around this by installing an user agent switcher with Internet Explorer 8, but I can't find such a switcher for Chrmium.

I will attach a print screen to see what I mean.
Thanks in advance!

---

### Post by Troll_the_Great on 2010-01-21
Bump!

---

### Post by Troll_the_Great on 2010-01-22
Bump!

---

### Post by zerwas on 2010-01-23
Please stop bumping.

Please uninstall the package
[LIST]
[*]**gecko-mediaplayer**
[/LIST]
Do you have these two packages installed?
[LIST]
[*]**[libquicktime1]("apt:libquicktime1")**
[*][B][totem-mozilla]("apt:totem-mozilla")
[/B][/LIST]
If not, install them.

Now right click an entry to download the movie and select "Open link in a new tab".

Good luck,
zerwas

---

### Post by Troll_the_Great on 2010-01-24
> **zerwas said:**
> Please stop bumping.

Please uninstall the package
[LIST]
[*]**gecko-mediaplayer**
[/LIST]
Do you have these two packages installed?
[LIST]
[*]**[libquicktime1]("apt:libquicktime1")**
[*][B][totem-mozilla]("apt:totem-mozilla")
[/B][/LIST]
If not, install them.

Now right click an entry to download the movie and select "Open link in a new tab".

Good luck,
zerwas

I only bumped once a day, which is allowed on these forums. 
I did what you said, but the only result I got was that I lost the ability to see trailers in firefox too, so I reverted the process.
I think I will never see those trailers in chromium...:(

---

### Post by zerwas on 2010-01-24
> **Troll_the_Great said:**
> I did what you said, but the only result I got was that I lost the ability to see trailers in firefox too, so I reverted the process.

Strange. But you didn't tell us what effect it had to right click and click on "Open link in a new tab" on the download entry of trailers.

---

### Post by Troll_the_Great on 2010-01-24
> **zerwas said:**
> Strange. But you didn't tell us what effect it had to right click and click on "Open link in a new tab" on the download entry of trailers.

If I click on "Open link in a new tab" it downloads the trailer.

---

### Post by zerwas on 2010-01-24
And you definitely have the package totem-mozilla and totem itself installed?

---

### Post by Troll_the_Great on 2010-01-25
> **zerwas said:**
> And you definitely have the package totem-mozilla and totem itself installed?

Definitely!

---

### Post by Troll_the_Great on 2010-01-28
Bump!

---

### Post by l-x-l on 2010-01-28
Funny but I'm having the opposite prob. I can see it in Chromium but not FF. Go figure.

---

### Post by Troll_the_Great on 2010-01-29
> **l-x-l said:**
> Funny but I'm having the opposite prob. I can see it in Chromium but not FF. Go figure.

Let's make a deal. I will help you see the trailers in firefox, and you will tell me how to see them in chromium. ;)
For firefox see this guide, that's how it worked for me:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Don't forget to read it all the way to the end, and edit pluginreg.dat (if you need to).
Your turn now :D

---

### Post by mc4man on 2010-01-29
> [QUOTE]And you definitely have the package totem-mozilla and totem itself installed? 
> Definitely! [/QUOTE]

what hasn't come up is what release of ubuntu you're using. The inability of the totem-mozilla plugin to play apple trailers was fixed in karmic only,  by default - no workarounds needed as in - 
> I firefox I got around this by installing an user agent switcher with Internet Explorer 8,



So here (on karmic), it works in firefox with the totem-mozilla plugin and in chromium which also uses the same  totem-mozilla plugin

It may be those that have playback **in the chromium browser** are using karmic

(the totem-mozilla plugin appears to be broken again in lucid in this regard

---

### Post by Troll_the_Great on 2010-01-29
> **mc4man said:**
> what hasn't come up is what release of ubuntu you're using. The inability of the totem-mozilla plugin to play apple trailers was fixed in karmic only,  by default - no workarounds needed as in - 




So here (on karmic), it works in firefox with the totem-mozilla plugin and in chromium which also uses the same  totem-mozilla plugin

It may be those that have playback **in the chromium browser** are using karmic

(the totem-mozilla plugin appears to be broken again in lucid in this regard

I am using Hardy Heron (as you can see under my avatar). So, from what you are saying, only people using Karmic can see apple trailers in chromium?

---

### Post by mc4man on 2010-01-29
> only people using Karmic can see apple trailers in chromium?
What I' saying is that in karmic the totem-mozilla plugin will by default be able to play apple trailers both in firefox and chromium.

In hardy it can't so you need a workaround (as you've seen ) for firefox and you'll need a workaround for chromium (as you've not yet seen) or a different plugin that does work - if there is one.

Only mentioned because sometimes people say - "it works here", (like I did earlier), not accounting for different ubuntu releases, plugins availabe, ect.
( I did see 8.04 below your avatar, though quite often people don't update that.

---

### Post by Troll_the_Great on 2010-01-30
> **mc4man said:**
> I did see 8.04 below your avatar, though quite often people don't update that.

No, I'm still using Hardy. I've tried for a few days Intreprid, but I didn't work so I reverted back to 8.04. I will stick with it until the next LTS arrives in April.

---

### Post by Troll_the_Great on 2010-02-04
Bump!

---

