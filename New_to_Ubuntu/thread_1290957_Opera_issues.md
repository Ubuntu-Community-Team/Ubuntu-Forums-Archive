---
title: "Opera issues"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by oohbuntoo on 2009-10-14
All of a sudden my Opera is lagging big time to load web pages.  It took like 39 seconds just to load the Ubuntu Forums front page!  And ESPN, fugettaboutit.  I thought maybe someone hacked into my router again, but speedtest.net shows I'm operating at the right speed.  As much as I didn't want to I booted Vista and internet there is running supa fast.  Also, MY SOUND IS GONNNNEEE!  I can't hear anything on the net.  No YouTube, Dailymotion, nothing.  However, I can still listen to music throught Rhythmbox.  I have no Idea what happened last night, but, something has changed, and I have no idea where to begin troubleshooting.

---

### Post by Arup on 2009-10-14
sudo apt-get --purge opera and install 10.10 beta latest from [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by Ekeluo on 2009-10-14
> The final release of opera 10 is out, why pointing to the beta? Go [here]("http://www.opera.com/download/").
Oops, didn't check b4 posting, assumed you were referring to a pre-v10 beta.

---

### Post by oohbuntoo on 2009-10-14
> **Arup said:**
> sudo apt-get --purge opera and install 10.10 beta latest from [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)
I tried to run that command and this is what I got:

stacks@ubuntu:~$ sudo apt-get --purge opera
[sudo] password for stacks: 
E: Invalid operation opera

---

### Post by Ekeluo on 2009-10-14
Should be ```
sudo apt-get --purge remove opera
```.

---

### Post by oohbuntoo on 2009-10-14
> **Ekeluo said:**
> Should be ```
sudo apt-get --purge remove opera
```.
O.k., I'm under the impression I have removed the Opera I had initially and installed Opera 10.  I ended the session and logged back in.  I still don't have sound and it is still dragging.  Following another link ( [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)) I have downloaded a package to my desktop [opera-10.10-4644.freebsd7-shared-qt3.amd64.tar.bz2] and I don't know what to do??

---

### Post by Ekeluo on 2009-10-14
Try other browsers, are they showing the same symptoms? Which version of ubuntu are you running? If you use synaptic to update, you should be able to get a history of upgraded packages; post them here (hint - use the code tag when pasting).

---

### Post by oohbuntoo on 2009-10-14
> **Ekeluo said:**
> Try other browsers, are they showing the same symptoms? Which version of ubuntu are you running? If you use synaptic to update, you should be able to get a history of upgraded packages; post them here (hint - use the code tag when pasting).
No luck in Firefox as far as the sound.  Does load SLIGHTLY faster than Opera is right now.  I'm just baffled at how everything worked just yesterday.  I haven't the slightest idea how to go about getting that list of upgraded packages.

Jaunty 9.04 Toshiba Satellite AMD 64

---

### Post by oohbuntoo on 2009-10-14
Just logged back into Jaunty.  My internet speed is back to normal, however, still no sound when watching YouTube, Dailymotion, etc..  I'm still at a loss as to what could be causing my volume/sound issue.  Also, I'm not sure how to install this Opera-10.10-4644.freebsd7-shared-qt3.amd64.tar.bz2 package I have saved to my desktop.

---

### Post by Perfect Storm on 2009-10-14
Opera-10.10-4644.freebsd7-shared-qt3.amd64.tar.bz2 is for FreeBSD not Linux.


Go here to grab Opera 10: [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by oohbuntoo on 2009-10-14
> **Artificial Intelligence said:**
> Opera-10.10-4644.freebsd7-shared-qt3.amd64.tar.bz2 is for FreeBSD not Linux.


Go here to grab Opera 10: [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)
Thanks A.I.!  Any ideas on what happened to my volume/sound for the internet??

---

### Post by Perfect Storm on 2009-10-14
> **oohbuntoo said:**
> Thanks A.I.!  Any ideas on what happened to my volume/sound for the internet??

Could be many things, when Opera is installed can you type 
```
about:plugins
```
in operas adresse box and post the output.

---

### Post by oohbuntoo on 2009-10-14
> **Artificial Intelligence said:**
> Could be many things, when Opera is installed can you type 
```
about:plugins
```
in operas adresse box and post the output.
I hope this is what you asked for:

Plug-ins
Shockwave Flashapplication/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/flashplugin-installer/libflashplayer.so

DivX Browser Plug-Invideo/divx	divx
video/vnd.divx	divx
/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

RealPlayer 9application/x-rpm	rpm
application/x-redhat-package	rpm
application/smil	smi,smil
application/x-pn-realmedia	rm
audio/x-pn-realaudio	ram,ra,rm
video/vnd.rn-realvideo	rv
application/vnd.rn-realmedia	rm,ra,ram
application/vnd.rn-realaudio	ra,ram
audio/x-realaudio	ra
audio/x-pn-realaudio-plugin	rpm
/usr/lib/mozilla/plugins/mplayerplug-in-rm.so

mplayerplug-in 3.55video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
video/mp4	mp4,mpg4
audio/mpeg	mp3,mp2,mpga,mpg,mpeg,mpa,abs,mpega
audio/mp3	mp3
audio/x-mpegurl	m3u,mp3
audio/basic	au,snd
video/3gpp	3gp,mp4
application/ogg	ogx,ogg
audio/ogg	oga,ogg,spx
audio/flac	flac
video/x-mpeg	mpg,mpeg,mpe
video/x-mpeg2	mpv2,mp2ve
audio/x-mpeg	mpg,mpeg,mpa,abs,mpega
audio/mpeg2	mp2
audio/x-mpeg2	mp2
audio/mp4	mp4,mpg4
audio/x-mp4	mp4
audio/mpeg3	mp3
audio/x-mpeg3	mp3
application/x-ogg	ogg,ogx
audio/x-ogg	ogg,oga
audio/x-flac	flac
video/fli	fli,flc
video/x-fli	fli,flc
video/x-flv	flv
video/vnd.vivo	viv,vivo
application/x-nsv-vp3-mp3	nsv
audio/x-mod	mod
audio/x-basic	au,snd
/usr/lib/mozilla/plugins/mplayerplug-in.so

VLC Multimedia Plugin (compatible Totem 2.26.1)audio/wav	wav
audio/x-wav	wav
video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
audio/mpeg	mp3,mp2,mpga,mpg,mpeg,mpa,abs,mpega
application/ogg	ogx,ogg
video/ogg	ogv
audio/ogg	oga,ogg,spx
application/annodex	anx
video/annodex	axv
audio/annodex	axa
application/x-ogg	ogg,ogx
audio/x-ogg	ogg,oga
video/x-flv	flv
application/x-nsv-vp3-mp3	nsv
video/x-ogg	ogg,ogv
video/flv	flv
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so

Windows Media Player Plug-inaudio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi,asf,wmv
application/asx	asx
video/x-ms-asf-plugin	asf,asx,asp,wmv
application/x-mplayer2	asf,asx,asp,avi,wma,wmv
video/x-ms-wm	wm,wmv
audio/x-ms-wma	wma
audio/x-ms-wax	wax
video/x-ms-wvx	wvx,wmv
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
video/msvideo	avi
application/x-ms-wmv	wmv
audio/x-ms-wmv	wmv
video/x-ms-wmp	wmp,wmv
application/x-ms-wmp	wmp
application/x-drm-v2	asx
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so

Adobe Reader 9.1application/pdf	pdf
application/vnd.adobe.xdp+xml	xdp
application/vnd.adobe.xfd+xml	xfd
application/vnd.fdf	fdf
application/vnd.adobe.xfdf	xfdf
/usr/lib/mozilla/plugins/nppdf.so

QuickTime Plug-in 7.2.0video/mp4	mp4,mpg4
image/x-pict	pict
video/quicktime	qt,mov,mp4,sdp
image/x-macpaint	pntg
image/x-quicktime	pict,pict1,pict2,mov
video/x-m4v	m4v
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so

Xine Pluginimage/png	png
image/x-png	png
audio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi,asf,wmv
video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
video/mp4	mp4,mpg4
audio/mpeg	mp3,mp2,mpga,mpg,mpeg,mpa,abs,mpega
audio/mp3	mp3
audio/x-mpegurl	m3u,mp3
audio/basic	au,snd
audio/x-aiff	aif,aiff
video/quicktime	qt,mov,mp4,sdp
application/vnd.ms-project	mpp
video/x-ms-asf-plugin	asf,asx,asp,wmv
application/x-mplayer2	asf,asx,asp,avi,wma,wmv
audio/x-ms-wma	wma
video/x-ms-wvx	wvx,wmv
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
application/smil	smi,smil
application/x-pn-realmedia	rm
audio/x-pn-realaudio	ram,ra,rm
application/ogg	ogx,ogg
video/ogg	ogv
audio/ogg	oga,ogg,spx
audio/flac	flac
application/annodex	anx
video/annodex	axv
audio/annodex	axa
application/xspf+xml	xspf
application/vnd.rn-realmedia	rm,ra,ram
application/vnd.rn-realaudio	ra,ram
audio/x-realaudio	ra
audio/x-pn-realaudio-plugin	rpm
video/x-mpeg	mpg,mpeg,mpe
audio/x-mpeg	mpg,mpeg,mpa,abs,mpega
audio/mpeg2	mp2
audio/x-mpeg2	mp2
audio/mp4	mp4,mpg4
audio/mpeg3	mp3
audio/x-mpeg3	mp3
application/x-ogg	ogg,ogx
audio/x-ogg	ogg,oga
audio/x-flac	flac
video/fli	fli,flc
video/x-fli	fli,flc
video/x-flv	flv
audio/x-mod	mod
audio/x-basic	au,snd
video/x-ogg	ogg,ogv
video/flv	flv
video/msvideo	avi
application/x-annodex	anx
audio/x-annodex	axa
video/x-annodex	axv
video/mkv	mkv
video/x-matroska	mkv
application/x-ogm	ogx
application/x-ogm-audio	oga
application/x-ogm-video	ogv
video/mng	mng
video/x-mng	mng
video/x-flic	fli,flc
audio/aiff	aif,aiff
audio/x-pn-aiff	aif,aiff
audio/x-pn-au	snd,au
audio/mod	mod
audio/it	it
audio/x-it	it
audio/x-stm	stm
audio/x-s3m	s3m
audio/s3m	s3m
application/playerpro	669
application/adrift	amf
audio/med	med
audio/x-amf	amf
audio/x-xm	xm
audio/xm	xm
audio/x-8svx	8svx
audio/8svx	8svx
audio/x-16sv	16sv
audio/168sv	16sv
image/x-ilbm	ilbm
image/ilbm	ilbm
video/x-anim	anim
video/anim	anim
application/x-flash-video	flv
application/vnd.ms-asf	asf
video/x-ms-wax	wva
audio/x-real-audio	ra,rm,ram
video/x-quicktime	mov,qt
audio/x-m4a	m4a,m4b
application/x-quicktimeplayer	qtl,mov
audio/x-pn-wav	wav
audio/x-pn-windows-acm	wav
audio/musepack	mpc,mp+,mpp
audio/x-musepack	mpc,mp+,mpp
audio/mpegurl	mp3
audio/x-mp3	mp3
audio/x-wavpack	wv,wvp
application/x-xine-plugin
/usr/lib/mozilla/plugins/xineplugin.so

DivXÂ® Web Playervideo/divx	divx
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so

Windows Media Player Plug-in 10 (compatible; Totem)video/x-msvideo	avi,asf,wmv
application/asx	asx
video/x-ms-asf-plugin	asf,asx,asp,wmv
application/x-mplayer2	asf,asx,asp,avi,wma,wmv
video/x-ms-wm	wm,wmv
audio/x-ms-wma	wma
video/x-ms-wvx	wvx,wmv
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
application/x-ms-wmv	wmv
audio/x-ms-wmv	wmv
video/x-ms-wmp	wmp,wmv
application/x-ms-wmp	wmp
video/x-wmv	wmv
application/x-ms-wms	wms
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so

QuickTime Plug-in 7.4.5video/quicktime	qt,mov,mp4,sdp
application/smil	smi,smil
image/x-quicktime	pict,pict1,pict2,mov
video/x-quicktime	mov,qt
application/x-quicktimeplayer	qtl,mov
/usr/lib/mozilla/plugins/mplayerplug-in-qt.so

Java(TM) Plug-in 1.6.0_16/usr/lib/mozilla/plugins/libjavaplugin.so

---

### Post by oohbuntoo on 2009-10-15
> **Artificial Intelligence said:**
> Could be many things, when Opera is installed can you type 
```
about:plugins
```
in operas adresse box and post the output.
O.k., now I have zero sound in Ubuntu.  No Rhythmbox, Banshee, Songbird, Stored movies, Opera, Firefox, Chromium.  I am completely lost as to what happened.  To quote a favorite song of mine, "it was all good just a week ago".  Yikes, I hope I don't have to bust a fresh install of Juanty.  I just got this thing runnin' the way I want.  Any ideas???

---

### Post by misfitpierce on 2009-10-15
Click the volume icon in taskbar and click sound settings and check to make sure pcm bar is up as well as the volume! If no go in that then try hitting system-pref-sound and then change them till you get a working one when you hit test and then restart to save everything in good order and check if its working all good.

---

### Post by Perfect Storm on 2009-10-16
It could also be, if you have two soundcards running at the same time. Eg. an onboard soundcard and a PCI soundcard. Then it's a good idea to disable the onboard soundcard in BIOS.

---

### Post by oohbuntoo on 2009-10-20
Well, I tried everything and nothing worked, so, I did a fresh install of Jaunty, installed Chromium.  Hopefully this won't die in a few months again! lol...

---

