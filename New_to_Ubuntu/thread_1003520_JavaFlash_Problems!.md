---
title: "Java/Flash Problems!"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Alexpants on 2008-12-06
I've had a scour of the forums and a blitz on Google but can't find a solution to my problem. 
Basically, I am currently running Ubuntu 8.10. I'm on an Acer 5520G laptop, which came pre-installed with Vista. I installed Ubuntu 8.04, wiping my Vista partition, then 8.10, then I decided I hated Ubuntu (noob error) and re-installed Vista after using the "clean all" function in DOS to completely wipe my hard drive. I installed Vista, then realised quite how good Ubuntu is, so re-installed 8.10 (my laptop hates me). 
So, I'm currently in the process of adding all the applications I like, reinstalling Wrath of the Lich King and customising my desktop to look exactly how I want. 
BUT. 
I can't get a lot of Java and Flash applications to work in my browser (firefox), which is a real problem as I use Weight Watchers online tools and their main points tracker runs on Java! I never had this problem before, I really can't think what's causing it! 
I've got;
Java 6 Runtime
Ubuntu Restriced Extras
Open JDK Java 6 Runtime
Open JDK Java 6 Web Start
Sun Java 6.0 Plugin
and
Icedtea Java Plugin

all installed but still nothing. Whenever I open a webpage using flash my screen dulls for a minute before not opening the java app at all. 
Help! Just to add, I'm a COMPLETE newbie, starting to et the hang of terminal after all of these installs but still pretty basic. I hope I've posted this in the right place! 
Thanks :)
-Lex

---

### Post by HotShotDJ on 2008-12-06
Using System --> Administration --> Synaptic Package Manager, please remove all openjdk and icedtea plugin.  Now, install sun-java6-plugin (if already installed, then mark for reinstallation and click the "apply" button).

Log out, then log back in (you shouldn't need to reboot, just log out of your user account)

Java should work now.

For flash, make sure that flashplugin-nonfree is installed.

---

### Post by Alexpants on 2008-12-06
Still no joy I'm afraid :( I still get the screen dulling and lack of app working!

---

### Post by HotShotDJ on 2008-12-06
> **Alexpants said:**
> Still no joy I'm afraid :( I still get the screen dulling and lack of app working!What is the web page... let me see if I have the same problem on my system.

---

### Post by Alexpants on 2008-12-06
[www.meez.com](www.meez.com) is one of them
But the main one is the weightwatchers.co.uk members site, however you will be unable to access the points tracker or main member page as it's a paid members only tool :(

---

### Post by HotShotDJ on 2008-12-06
No problem for me on Meez (although I didn't do much while I was there)

As far as Java is concerned, there are a couple things we can look at.  First, I'd like you to open a terminal (Applications --> Accessories --> Terminal) and then type:```
sudo update-java-alternatives --list
```What is the output of that command?

---

### Post by Alexpants on 2008-12-06
The output I got was...
java-6-sun 63 /usr/lib/jvm/java-6-sun

Feel a little bit sad admitting I like meez! Damn addictive site... ;)

---

### Post by gandaran on 2008-12-06
I didn't see any java applets in weightwatchers.co.uk and meez only flash!
check what you have installed for flash, gnash, swfdec or adobe!, you must only use one flash type and the best is adobe flash 10

---

### Post by HotShotDJ on 2008-12-06
> **Alexpants said:**
> The output I got was...
java-6-sun 63 /usr/lib/jvm/java-6-sun

Feel a little bit sad admitting I like meez! Damn addictive site... ;)Ok, that output is what it is supposed to be.

I have seen reports of some sites that use Java not being compatible with Java 6 but work just fine with Java 5.  Lets see if that is the problem with weight watchers.

Go ahead and open Synaptic Package Manager and install sun-java5-plugin.  You do NOT have to remove sun-java6.  Once that is done, log out of your user account and then log back in. Go back to your terminal and run sudo update-java-alternatives --list.  Both java-6 and java-5 should be listed.  Now type in```
update-java-alternatives --set java-1.5.0-sun
```(IMPORTANT, make sure to change java-1.5.0-sun to match the output of the --list command, it might be java-5-sun... I can't remember for sure)

Log out and back in.  Fire up Firefox.  Check which version of Java it is using by typing about:plugins where you normally type in a web address.  If the correct version shows up (something like Java(TM) Plug-in 1.5.0) then check out weight watchers.

Let me know what happens.

---

### Post by Alexpants on 2008-12-06
Ok, I've tried that (I also tried re-installing adobe flash 10 as per gandaran's reply) but still no luck! 
It's telling me I'm still running "Java(TM) Plug-in 1.6.0_10-b33"

---

### Post by HotShotDJ on 2008-12-06
Standby... testing on my system to see where my instructions went wrong.

Ok, I'm having no trouble... I installed sun-java5-plugin and I'm able to switch between java6 and java5 using the following commands:
```
sudo update-java-alternatives --set java-1.5.0-sun
sudo update-java-alternatives --set java-6-sun
```(The logout and back in is actually not necessary to get firefox to pick up the change)

I'm at a loss.... I'm sorry I couldn't get you up and running with this.

---

### Post by gandaran on 2008-12-06
> **Alexpants said:**
> Ok, I've tried that (I also tried re-installing adobe flash 10 as per gandaran's reply) but still no luck! 
It's telling me I'm still running "Java(TM) Plug-in 1.6.0_10-b33"
but did you check for any other flash installed? mozilla-plugin-gnash or mozilla-swfdec-plugin

---

### Post by Alexpants on 2008-12-06
> **gandaran said:**
> but did you check for any other flash installed? mozilla-plugin-gnash or mozilla-swfdec-plugin

I thought i'd removed mozilla-swfdec-plugin but it seems I hadn't. I did that and rebooted firefox, I can now get the WW page to load faster, however I still can't access the points tracker. D'oh!

[EDIT] After a re-boot of my machine the points tracker is now working, but still no meez!

---

### Post by gandaran on 2008-12-06
Alexpants
can you you post the output of typing this code in firefox url bar
```
about:plugins
```

---

### Post by Alexpants on 2008-12-06
> **gandaran said:**
> Alexpants
can you you post the output of typing this code in firefox url bar
```
about:plugins
```

The whole output is...

```

Java(TM) Plug-in 1.6.0_10-b33

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_10

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
application/x-java-applet;jpi-version=1.6.0_10 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_10 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
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
Totem Web Browser Plugin 2.24.3

    File name: libtotem-basic-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	application/annodex type 	anx 	Yes
audio/annodex 	audio/annodex type 	axa 	Yes
video/annodex 	video/annodex type 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

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
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

```

---

### Post by saeid on 2009-05-09
> **HotShotDJ said:**
> Using System --> Administration --> Synaptic Package Manager, please remove all openjdk and icedtea plugin.
Thank you, It's work for me. :)

---

